<script setup>
import "./social.scss";
import GreenBtn from "@/components/UIbuttons/greenBtn/greenButton.vue";
import SocialCard from "@/components/UICard/social-card/socialCard.vue";

import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';

import 'swiper/css';
import 'swiper/css/navigation';

const modules = [Navigation, Pagination, Scrollbar, A11y];

</script>

<template>
    <div class="socials">
        <div class="socials__container container">
            <div class="socials__title">
                <h1 class="socials__title title">Соцсеть для бизнеса</h1>
                <p class="subtitle">
                    Станьте участником крупнейшей сети B2B сообщества в крупнейших
                    отраслях экономики Российской Федерации.
                </p>
            </div>
            <div class="socials__slide">
                <swiper :modules="modules"
                    :navigation="{ nextEl: '.socials__arrow--right', prevEl: '.socials__arrow--left' }"
                    :grab-cursor="true" 
                    :slides-per-view="4" 
                    :space-between="16" 
                    >
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                    <swiper-slide>
                        <SocialCard />
                    </swiper-slide>
                </swiper>
            </div>
            <div class="socials__buttons">
                <GreenBtn>Присоединиться →</GreenBtn>
                <div class="socials__arrows">
                    <div class="socials__arrow socials__arrow--left">
                        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M15.41 16.58L10.83 12L15.41 7.41L14 6L8 12L14 18L15.41 16.58Z" fill="white" />
                        </svg>
                    </div>
                    <div class="socials__arrow socials__arrow--right">
                        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M8.59 16.58L13.17 12L8.59 7.41L10 6L16 12L10 18L8.59 16.58Z" fill="white" />
                        </svg>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
