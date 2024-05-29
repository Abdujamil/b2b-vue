<script setup>
import "./social.scss";
import GreenBtn from "@/components/UIbuttons/greenBtn/greenButton.vue";
import SocialCard from "@/components/UICard/social-card/socialCard.vue";

import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
const socialSwiper = {
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        return {
            onSwiper,
            onSlideChange,
            modules: [Pagination, A11y, Navigation],
        };
    }
};
</script>

<template>
    <div id="socials" class="socials">
        <div class="socials__container container">
            <div class="socials__title">
                <h1 class="socials__title title">Соцсеть для бизнеса</h1>
                <p class="subtitle">
                    Станьте участником крупнейшей сети B2B сообщества в крупнейших
                    отраслях экономики Российской Федерации.
                </p>
            </div>
            <div class="socials__slide">
                <swiper 
                :modules="modules" 
                :slides-per-view="4" 
                :space-between="16"
                @swiper="socialSwiper" 
                @slideChange="onSlideChange"
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
                <div class="socials__arrows" navigation>
                    <div class="swiper-button-prev socials__arrow socials__arrow--left"></div>
                    <div class="swiper-button-next socials__arrow socials__arrow--right"></div>
                </div>
            </div>
        </div>
    </div>

</template>

<style scoped></style>