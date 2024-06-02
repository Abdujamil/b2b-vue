<script setup>
import { ref, computed } from 'vue';
import CustomCard from '@/components/UICard/custom-card/customCard.vue';
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue';
import './b2b.scss'

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

                <button 
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
                </button>
            </div>

            <div class="b2b-cards">
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
            </div>
            <CustomBtn :href="birzhaLink" />
        </div>
    </div>

</template>

<style scoped></style>