<script setup>
import { ref, onMounted } from 'vue';


import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
import axios from 'axios';

import 'swiper/css';
import 'swiper/css/navigation';

import fulfilmentSvg from '@/assets/images/fulfilment.svg'
import birzhaSvg from '@/assets/images/birzhaSvg.svg'
import electronTorgSvg from '@/assets/images/electronTorgSvg.svg'
import impotSvg from '@/assets/images/impotSvg.svg'
import birzhaFrilanceSvg from '@/assets/images/birzhaFrilanceSvg.svg'
import socialBuisnessSvg from '@/assets/images/socialBuisnessSvg.svg'
import b2bSvg from '@/assets/images/b2bSvg.svg'
import LearnMoreSvg from '@/assets/images/LearnMoreSvg.svg'

import slideCard from '@/components/UICard/slider-card/sliderCard.vue'
import IntroHead from '@/components/b2b/intro/intro-header/intro-header.vue';
import introCard from '@/components/b2b/intro/intro-card/introCard.vue';

const modules = [Navigation, Pagination, Scrollbar, A11y];

const cards = ref([]);
const loading = ref(true);

const fetchData = async () => {
    try {
        const response = await axios.request({
            method: 'get',
            maxBodyLength: Infinity,
            url: '/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=20',
            headers: {
                'Authorization': 'Bearer z8NQIIfEd882hvkP83WoOPJEqfCxMu42',
                'Cookie': '55e884495441419f79abfcee0eb88317=050cb5ef2d9397eb2cd7dc471bc260c8'
            }
        });
        cards.value = response.data;
    } catch (error) {
        console.error('Ошибка при загрузке данных:', error);
    } finally {
        loading.value = false;
    }
};

onMounted(() => {
    fetchData();
});

</script>

<template>
    <div class="intro">
        <div class="intro__container container">

            <IntroHead />

            <div class="intro__body">
                <div class="intro__title">
                    <h1 class="intro__title-text">
                        B2B <br />
                        Search Engine
                    </h1>
                    <p class="intro__subtitle subtitle">Помощник в вашем бизнесе.</p>
                </div>
                <div class="intro__buttons">
                    <a href="#" class="button__link">Смотреть обучающее видео</a>
                    <a href="#" class="button__link">Зарегистрироваться</a>
                </div>
            </div>

            <div class="intro__slider">

                <div class="home__slider-header">
                    <h1 class="home__slider-title title">Что мы предлагаем?</h1>
                    <p class="home__slider-subtitle subtitle">Инструмент для решения каждодневных задач.</p>
                </div>

                <swiper 
                    :modules="modules"
                    :navigation="{ 
                        nextEl: '.intro__swiper-button-next', 
                        prevEl: '.intro__swiper-button-prev' 
                    }"
                    :grab-cursor="true" 
                    :slides-per-view="3" 
                    :space-between="16" 
                    @swiper="onSwiper"
                @slideChange="onSlideChange"
                >
                    <swiper-slide>
                        <introCard
                        :image="fulfilmentSvg"
                        title="Фулфилмент"
                        description="Размещайте свои товары на наших складах"
                        />
                        <introCard
                        :image="birzhaSvg"
                        title="Биржа грузоперевозок"
                        description="Перевозка и доставка груза по России"
                        />
                    </swiper-slide>
                    <swiper-slide>
                        <introCard
                        :image="b2bSvg"
                        title="Фулфилмент"
                        description="Размещайте свои товары на наших складах"
                        />
                        <introCard
                        :image="birzhaFrilanceSvg"
                        title="Биржа грузоперевозок"
                        description="Перевозка и доставка груза по России"
                        />
                    </swiper-slide>
                    <swiper-slide>
                        <introCard
                        :image="electronTorgSvg"
                        title="Фулфилмент"
                        description="Размещайте свои товары на наших складах"
                        />
                        <introCard
                        :image="impotSvg"
                        title="Биржа грузоперевозок"
                        description="Перевозка и доставка груза по России"
                        />
                    </swiper-slide>
                    <swiper-slide>
                        <introCard
                        :image="socialBuisnessSvg"
                        title="Фулфилмент"
                        description="Размещайте свои товары на наших складах"
                        />
                        <introCard
                        :image="LearnMoreSvg"
                        title="Биржа грузоперевозок"
                        description="Перевозка и доставка груза по России"
                        />
                    </swiper-slide>

                    <div class="intro__swiper-button-next">
                        <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg"
                            style="flex-grow: 0; flex-shrink: 0; width: 32px; height: 32px; position: relative;"
                            preserveAspectRatio="xMidYMid meet">
                            <path
                                d="M11.4533 22.1067L17.56 16L11.4533 9.88L13.3333 8L21.3333 16L13.3333 24L11.4533 22.1067Z"
                                fill="#1E2B3E"></path>
                        </svg>
                    </div>
                    <div class="intro__swiper-button-prev">
                        <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg"
                            style="flex-grow: 0; flex-shrink: 0; width: 32px; height: 32px; position: relative;"
                            preserveAspectRatio="xMidYMid meet">
                            <path
                                d="M20.5467 22.1067L14.44 16L20.5467 9.88L18.6667 8L10.6667 16L18.6667 24L20.5467 22.1067Z"
                                fill="#1E2B3E"></path>
                        </svg>
                    </div>
                </swiper>

            </div>
        </div>
    </div>
</template>


<style scoped></style>