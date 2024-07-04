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
<!-- 
<div class="home_body_btns invite_text">
    <h2 class="title"> Приглашаем поставщиков к сотрудничеству! </h2>
 <h2 class="title"> Регистрируйте свою компанию и продавайте товары и услуги в нашей бизнес-экосистеме.</h2>
</div> -->

<template>
        <div class="b2b-card" v-if="customCard">
            <div class="b2b-card__slide">
                <Swiper :modules="modules" :slides-per-view="1" :space-between="50" :pagination="{ clickable: true }">
                    <SwiperSlide>
                        <img v-if="customCard.image && customCard.image.startsWith('https://market.b2b-se.com/components/com_jshopping/files/img_products/')"
                            :src="customCard.image" alt="Product Image">
    
                        <img v-else-if="customCard.image"
                            :src="'https://market.b2b-se.com/components/com_jshopping/files/img_products/' + customCard.image"
                            alt="Product Image">
    
                        <img v-else
                            src="https://market.b2b-se.com/components/com_jshopping/files/img_products/b2b_se_logo_full_blue.png"
                            alt="Default Image">
                            
                    </SwiperSlide>
                </Swiper>
            </div>
            <div class="b2b-card__title">
                <h3>{{ customCard['name_ru-RU'] || customCard['name'] || 'Без названия' }}</h3>
                <p>{{ customCard['short_description_ru-RU'] || customCard['short_description'] || '' }}</p>
            </div>
            <div class="b2b-card__card-price">
                <h3>{{ customCard['product_price'] || 'Цена не указана' }} ₽<span>{{ customCard['product_old_price'] || ''
                        }}₽</span></h3>
                <p>за 1 м</p>
            </div>
            <div class="b2b-card__card-km">
                <div class="card-city">
                    <h3 id="selectedCity">Москва</h3>
                </div>
            </div>
        </div>
</template>
