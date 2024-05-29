<script setup>
import CardImg from "@/assets/images/no-img.png";
import './customCard.scss';
import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
const swiperB2b = {
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        return {
            onSwiper,
            onSlideChange,
            modules: [Pagination, A11y],
        };
    }
};
</script>

<template>
    <div class="b2b-card">
        <div class="b2b-card__slide">
            <div class="swiper b2bslider">
                <swiper 
                :modules="modules"
                :slides-per-view="1"
                :space-between="50"
                :pagination="{ clickable: true }"
                @swiper="swiperB2b"
                @slideChange="onSlideChange"
                >
                    <swiper-slide><img :src="CardImg" alt="img" /></swiper-slide>
                    <swiper-slide><img :src="CardImg" alt="img" /></swiper-slide>
                    <swiper-slide><img :src="CardImg" alt="img" /></swiper-slide>
                </swiper>
            </div>
        </div>
        <div class="b2b-card__title">
            <h3>Высокопрочная кабельная труба спиральная многок...</h3>
            <p>ООО «Восток»</p>
        </div>
        <div class="b2b-card__card-price">
            <h3>890 ₽ <span>9 564 ₽</span></h3>
            <p>за 1 м</p>
        </div>
        <div class="b2b-card__card-km">
            <div class="card-city">
                <h3 id="selectedCity">Москва</h3>
            </div>
        </div>
    </div>
</template>
