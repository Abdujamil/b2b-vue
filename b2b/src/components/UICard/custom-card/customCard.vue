<script setup>
import CardImg from "@/assets/images/no-img.png";
import './customCard.scss';
import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';

import { Swiper, SwiperSlide } from 'swiper/vue';
                    
import 'swiper/css';
import 'swiper/css/pagination';

const modules = [Navigation, Pagination, Scrollbar, A11y];

defineProps({
    customCard: {
        type: Object,
        required: true
    }
});

</script>

<template>
    <div class="b2b-card " v-if="customCard">
        <div class="b2b-card__slide">
            <Swiper 
                :modules="modules" 
                :slides-per-view="1" 
                :space-between="50" 
                :pagination="{ clickable: true }"
                @swiper="onSwiper" 
                @slideChange="onSlideChange"
            >
                <SwiperSlide><img :src="CardImg" alt="img" /></SwiperSlide>
                <SwiperSlide><img :src="CardImg" alt="img" /></SwiperSlide>
                <SwiperSlide><img :src="CardImg" alt="img" /></SwiperSlide>
            </Swiper>
        </div>
        <div class="b2b-card__title">
            <h3>{{  typeof(customCard.alias_ru-RU) }}</h3>
            <p>{{ typeof(customCard.description_ru-RU) }}</p>
        </div>
        <div class="b2b-card__card-price">
            <h3>{{ customCard.product_price }} ₽<span>{{ customCard.product_old_price }}₽</span></h3>
            <p>за 1 м</p>
        </div>
        <div class="b2b-card__card-km">
            <div class="card-city">
                <h3 id="selectedCity">Москва</h3>
            </div>
        </div>
    </div>
</template>
