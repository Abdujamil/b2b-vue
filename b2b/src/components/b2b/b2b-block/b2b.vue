<script setup>
import { ref, computed, onMounted } from 'vue';
import CustomCard from '@/components/UICard/custom-card/customCard.vue';
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue';
import './b2b.scss'
import axios from 'axios';

const cards = ref([]);
const loading = ref(true);

const birzhaLink = '#';

const fetchData = async () => {
    try {
        const response = await axios.request({
            method: 'get',
            maxBodyLength: Infinity,
            url: '/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=16',
            headers: {
                'Authorization': 'Bearer 8RglvgmiGNiUHJZ8fXMqJX6M1qLoUkpq',
                'Cookie': '55e884495441419f79abfcee0eb88317=3f8e9bfc58965ce9a71102682b41b122'
            }
        });

        // Проверяем, является ли response.data объектом
        if (typeof response.data === 'object') {
            // Преобразуем объект в массив значений и обновляем значение cards.value
            const objectsArray = Object.values(response.data).filter(item => typeof item === 'object');

            // Модифицируем объекты в массиве, чтобы они имели свойство 'alias_ru-RU'
            const updatedCards = objectsArray.map((product) => {
                return {
                    alias_ru_RU: product[3]['alias_ru-RU'],
                    description_ru_RU: product[3]['description_ru-RU'],
                    product_price: product[3]['product_price'],
                    product_old_price: product[3]['product_old_price'],
                    // Другие свойства продукта, которые могут быть необходимы
                };
            });

            // Обновляем cards.value с помощью новых данных
            cards.value = updatedCards;
        } else {
            throw new Error('Данные не являются объектом');
        }
    } catch (error) {
        console.error('Ошибка при загрузке данных:', error);
    } finally {
        loading.value = false;
    }
};




onMounted(() => {
    fetchData();
});


const maxVisibleButtons = ref(12);
const buttons = ref([
    'Все рубрики',
    'Офис / Все для офиса',
    'Техника',
    'Строительство и ремонт',
    'Транспорт и логистика',
    'Безопасность',
    'Легкая промышленность',
    'Пищевая промышленность',
    'Электроэнергетика',
    'Металлургия',
    'Реклама'
]);

const showAll = ref(false);
const activeButton = ref('Все рубрики');  // По умолчанию активна первая кнопка

const visibleButtons = computed(() => {
    return showAll.value ? buttons.value : buttons.value.slice(0, maxVisibleButtons.value);
});

const hasMoreButtons = computed(() => {
    return buttons.value.length > maxVisibleButtons.value;
});

function toggleShowAll() {
    showAll.value = !showAll.value;
}

function setActiveButton(button) {
    activeButton.value = button;
}
</script>



<template>
    <div class="b2b">
        <div class="b2b__container container">
            <div class="b2b__title">
                <h2 class="title">B2B Рынок</h2>
                <p class="subtitle">Топ товаров по разделам.</p>
            </div>

            <div class="b2b__filter-categories">
                <button v-for="(button, index) in visibleButtons" :key="index"
                    :class="['btn', 'filter-category', { active: activeButton === button }]"
                    @click="setActiveButton(button)">
                    {{ button }}
                </button>

                <button v-if="hasMoreButtons && !showAll" class="btn showMoreBtn" @click="toggleShowAll">
                    Показать еще...
                </button>

                <button v-if="hasMoreButtons && showAll" class="btn filter-category" @click="toggleShowAll">
                    Скрыть
                </button>
            </div>

            <div class="b2b-cards">
                <CustomCard v-for="(card, index) in cards" :key="index" :customCard="card" />
                <!-- {{ cards[0].alias_ru_RU }} -->
            </div>
            <CustomBtn :href="birzhaLink" />
        </div>
    </div>

</template>

<style scoped></style>