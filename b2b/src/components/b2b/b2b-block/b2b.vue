<script setup>
import { ref, computed, onMounted } from 'vue';
import CustomCard from '@/components/UICard/custom-card/customCard.vue';
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue';
import './b2b.scss';
import axios from 'axios';

const cards = ref([]);
const categories = ref([]);
const loading = ref(true);
const activeButton = ref('Все рубрики');
const selectedCategory = ref(null);
const defaultLimit = 8; 

const fetchData = (url) => {
  return new Promise((resolve, reject) => {
    axios.request({
      method: 'get',
      maxBodyLength: Infinity,
      url: url,
      headers: {
        'Authorization': 'Bearer JOTPLtopM2z8OF4Q8QQSxgAY1fL52qn3',
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
      console.log('Products:', results[0], 
        'Product_ID', results[1]['2']['category_parent_id']
      );
      console.log('Categories:', results[1]);
      cards.value = results[0];
      categories.value = results[1];
      loading.value = false;
    }).catch(error => {
      console.error('Error loading data:', error);
      loading.value = false;
    });
});

const fetchFilteredCards = (categoryId) => {
  loading.value = true;

  const url = categoryId ? 
    `/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=search&args[categories][]=${categoryId}` : `/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=${defaultLimit}`;
  
  fetchData(url)
    .then(result => {
      if (Array.isArray(result)) {
        result.forEach((item, index) => {
          if (typeof item !== 'object') {
            console.error(`Item at index ${index} is not an object:`, item);
          }
        });
      }
      
      cards.value = result['products']; 
      console.log(result);
      loading.value = false;
    })
    .catch(error => {
      console.error('Error fetching filtered data:', error);
      loading.value = false;
    });
};

function setActiveButton(category) {
  activeButton.value = category['name_ru-RU'];
  selectedCategory.value = category;

  fetchFilteredCards(category['category_parent_id']);
  console.log(category['category_parent_id'] === 0);
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
        <!-- <button v-for="(category, index) in categories" 
          :data-id="category['category_parent_id']"
          :key="index" 
          :class="['btn', 'filter-category', { active: activeButton === category['name_ru-RU'] }]" 
          @click="setActiveButton(category)">
          <div v-if="category['category_parent_id'] === 0">
             {{ category['name_ru-RU'] }}
          </div>
          <div v-else>
            {{ category['name_ru-RU'] }}
          </div>
        </button> -->

        <div v-for="(category, index) in categories" :key="index">
          <button  
          v-if="category['category_parent_id'] === 0" 
          :class="['btn', 'filter-category', { active: activeButton === category['name_ru-RU'] }]" 
          @click="setActiveButton(category)"
          >
            {{ category['name_ru-RU'] }}
          </button>
        </div>
      </div>

      <div class="b2b-cards" v-if="!loading">
        <template v-if="cards">
          <CustomCard v-for="(card, index) in cards" :key="index" :customCard="card" />
        </template>
      </div>
      

      <div class="loading" v-else>Загрузка...</div>

      <CustomBtn :href="birzhaLink" />
    </div>
  </div>
</template>

<style scoped>

.loading{
  height: 200px;
  width: 100%;
}
</style>