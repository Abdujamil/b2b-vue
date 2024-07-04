<script setup>
import { ref, onMounted } from 'vue';
import CustomCard from '@/components/UICard/custom-card/customCard.vue';
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue';
import './b2b.scss';
import axios from 'axios';

const cards = ref([]);
const categories = ref([]);
const loading = ref(true);
const activeButton = ref('Все рубрики');
const selectedCategory = ref(null);
const defaultLimit = 12;

const fetchData = (url) => {
  return new Promise((resolve, reject) => {
    axios.request({
      method: 'get',
      maxBodyLength: Infinity,
      url: url,
      headers: {
        'Authorization': 'Bearer WxUMXyMaancekek0lEE6nsSU5jLvMy8T',
      }
    }).then(response => {
      resolve(response.data['result']);
    }).catch(error => {
      console.error('Error fetching data:', error);
      reject(error);
    });
  });
};

const productsFetch = fetchData(`/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=${defaultLimit}`);
const productsCategory = fetchData('/api/index.php?option=com_jshopping&controller=addon_api&section=category&task=list&args');

onMounted(() => {
  Promise.all([productsFetch, productsCategory])
    .then(results => {
      cards.value = results[0];
      categories.value = results[1];
      loading.value = false;
    }).catch(error => {
      console.error('Error loading data:', error);
      loading.value = false;
    });
});

const fetchCategoryProducts = async (categoryId) => {
  const url = `/api/index.php?option=com_jshopping&controller=addon_api&section=category&task=tree`;
  const result = await fetchData(url);
  // console.log(result);
  return result;
};

const getAllItems = async (category) => {
  let items = [];

  const traverse = async (category) => {
    const categoryItems = await fetchCategoryProducts(category['category_id']);
    items = items.concat(categoryItems);
    // console.log(items);

    if (category['subcategories']) {
      for (let subcategory of Object.values(category['subcategories'])) {
        await traverse(subcategory);
      }
    }
  };

  await traverse(category);
  return items;
};

function setActiveButton(category) {
  activeButton.value = category['name_ru-RU'];
  console.log(category['category_id']);
  selectedCategory.value = category;
  console.log(selectedCategory.value);

  loading.value = true;

  getAllItems(category).then(allItems => {
    console.log('All items:', allItems[0]); 
    
    cards.value = allItems[0];
    loading.value = false;

  }).catch(error => {
    console.error('Error fetching all items:', error);
    loading.value = false;
  });
}

const birzhaLink = 'https://market.b2b-se.com/';
</script>

<template>
  <div class="b2b">
    <div class="b2b__container container">
      <div class="b2b__title">
        <h2 class="title">B2B Рынок</h2>
        <p class="subtitle">Топ товаров по разделам.</p>
      </div>

      <div class="b2b__filter-categories">
        <div v-for="(category, index) in categories" :key="index">
          <button v-if="category['category_parent_id'] === 0"
            :class="['btn', 'filter-category', { active: activeButton === category['name_ru-RU'] }]"
            @click="setActiveButton(category)">
            {{ category['name_ru-RU'] }}
          </button>
        </div>
      </div>

      <div class="b2b-cards" v-if="!loading">
        <template v-if="cards">
          <CustomCard v-for="(card, index) in cards" :key="index" :customCard="card" />
        </template>
      </div>

      <div class="loading" v-else>
        <div class="jawn"></div>
      </div>

      <CustomBtn :href="birzhaLink" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.loading {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  // backdrop-filter: blur(5px);
  background: #000000c9;
  z-index: 99998;
  display: flex;
  align-items: center;
  justify-content: center;


  .jawn {
    position: relative;
    background-color: #F8E71C;
    width: 10px;
    height: 10px;
    margin: 0 auto;
    border-radius: 50%;

    &:after,
    &:before {
      content: "";
      position: absolute;
      width: 5px;
      height: 5px;
      border-radius: 50%;
    }

    &:after {
      left: -10px;
      top: -5px;
      background-color: #C7C2A6;
      transform-origin: 15px 10px;
      animation: axis 1s linear infinite;
    }

    &:before {
      left: -25px;
      top: -15px;
      background-color: rgb(0, 155, 255);
      transform-origin: 30px 20px;
      animation: axis 2s linear infinite;
    }
  }
}

@keyframes axis {
  0% {
    transform: rotateZ(0deg) translate3d(0, 0, 0);
  }

  100% {
    transform: rotateZ(360deg) translate3d(0, 0, 0);
  }
}
</style>