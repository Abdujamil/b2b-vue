<script setup>
import { ref, computed, onMounted } from 'vue';
import CustomCard from '@/components/UICard/custom-card/customCard.vue';
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue';
import './b2b.scss'
import axios from 'axios';


const cards = ref([]);
const categories = ref([]);
const loading = ref(true);

const fetchData = async (url) => {
  try {
    const response = await axios.request({
      method: 'get',
      maxBodyLength: Infinity,
      url: url,
      headers: {
        'Authorization': 'Bearer FplEpXNhy6bB6zFB3MY5imiOONczyTNu',
        'Cookie': '55e884495441419f79abfcee0eb88317=afd996b6e0110c80528334c19cf8a64a'
      }
    });

    cards.value = response.data['result'];

    categories.value = response.data['result'];

    console.log(response.data)
  } catch (error) {
    console.error('Ошибка при загрузке данных:', error);
  } finally {
    loading.value = false;
  }
};


onMounted(() => {
  fetchData('/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=12');
  fetchData('/api/index.php?option=com_jshopping&controller=addon_api&section=category&task=list&args[limit]=10');
});


// const maxVisibleButtons = ref(12);
// const buttons = ref([
//     'Все рубрики',
//     'Офис / Все для офиса',
//     'Техника',
//     'Строительство и ремонт',
//     'Транспорт и логистика',
//     'Безопасность',
//     'Легкая промышленность',
//     'Пищевая промышленность',
//     'Электроэнергетика',
//     'Металлургия',
//     'Реклама'
// ]);

const showAll = ref(false);
const activeButton = ref('Все рубрики');  // По умолчанию активна первая кнопка

// const visibleButtons = computed(() => {
//     return showAll.value ? buttons.value : buttons.value.slice(0, maxVisibleButtons.value);
// });

// const hasMoreButtons = computed(() => {
//     return buttons.value.length > maxVisibleButtons.value;
// });

// function toggleShowAll() {
//     showAll.value = !showAll.value;
// }

function setActiveButton(button) {
    activeButton.value = button;
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
                <!-- <button v-for="(button, index) in visibleButtons" :key="index"
                    :class="['btn', 'filter-category', { active: activeButton === button }]"
                    @click="setActiveButton(button)">
                    {{ button }}
                </button> -->

                <button
                v-for="(category, index) in categories"
                :key="index"
                :class="['btn', 'filter-category', 
                { active: activeButton === category }]"
                @click="setActiveButton(category)"
                >
                     {{ category['name_ru-RU']  }}
                </button>

                <!-- <button 
                v-if="hasMoreButtons && !showAll" 
                class="btn showMoreBtn" 
                @click="toggleShowAll"
                >
                    Показать еще...
                </button>

                <button 
                v-if="hasMoreButtons && showAll" 
                class="btn filter-category" 
                @click="toggleShowAll"
                >
                    Скрыть
                </button> -->
            </div>

            <div class="b2b-cards">
                <CustomCard v-for="card in cards" :key="card.id" :customCard="card" />
            </div>
            <CustomBtn :href="birzhaLink" />
        </div>
    </div>

</template>

<style scoped></style>