<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

import logo from '@/assets/images/logo.svg'
import search from '@/assets/images/search.svg';
import loginIcon from '@/assets/images/loginIcon.svg';
import favorites from '@/assets/images/favorites.svg';
import deals from '@/assets/images/deals.svg';
import catalogIcon from '@/assets/images/catalogIcon.svg';

import closeBtn from '@/assets/images/close.svg';
import burgerBtn from '@/assets/images/burger.svg';

// const isMenuOpen = ref(false);

// const toggleMenu = () => {
//   isMenuOpen.value = !isMenuOpen.value;
// };

// const handleResize = () => {
//   const header = document.querySelector('.header');
//   if (window.innerWidth > 768) {
//     header.style.display = 'none';
//   } else {
//     header.style.display = 'block';
//   }
// };

// onMounted(() => {
//   handleResize();
//   window.addEventListener('resize', handleResize);
// });

// onBeforeUnmount(() => {
//   window.removeEventListener('resize', handleResize);
// });
</script>

<template>
    <div class="intro__header">
        <div class="intro__left">
            <a href="#" class="intro__logo-link">
                <img class="intro__logo" :src="logo" alt="logo" />
            </a>
            <div class="intro__catalog">
                <a class="button button--catalog">
                    <img :src="catalogIcon" alt="catalogIcon" class="intro__catalog-icon" />Каталог
                </a>
            </div>
        </div>
        <div class="intro__search-box">
            <input type="text" class="intro__search-input" placeholder="Поиск для бизнеса" />
            <a class="button button--search">
                <img :src='search' alt="search" class="intro__search-icon" />
            </a>
            <img 
            :src="burgerBtn" 
            @click="toggleMenu" 
            alt="burger" 
            class="header__btn header__open-btn" 
            v-if="!isMenuOpen"
            >
        </div>
        <div class="intro__btns">
            <div class="intro__btn intro__login">
                <div class="intro__login-icon">
                    <img :src="loginIcon" alt="loginIcon" />
                </div>
                <a id="login" class="button button--login">Войти</a>
            </div>
            <div class="intro__btn intro__favorites">
                <div class="intro__favorites-icon">
                    <img :src="favorites" alt="favorites" />
                </div>
                <a id="favorites" class="button button--favorites">Избранное</a>
            </div>
            <div class="intro__btn intro__deals">
                <div class="intro__deals-icon">
                    <img :src="deals" alt="deals" />
                </div>
                <a id="deals" class="button button--deals">Сделки</a>
            </div>

            <div class="intro__btn intro__cat">
                <div class="intro__deals-icon">
                    <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M16.56 14.9L19.64 18L18.25 19.39L15.13 16.32C14.44 16.75 13.62 17 12.75 17C10.25 17 8.25 15 8.25 12.5C8.25 10 10.25 8 12.75 8C15.25 8 17.25 10 17.25 12.5C17.25 13.38 17 14.21 16.56 14.9ZM12.75 15C14.13 15 15.25 13.88 15.25 12.5C15.25 11.12 14.13 10 12.75 10C11.37 10 10.25 11.12 10.25 12.5C10.25 13.88 11.37 15 12.75 15ZM18.25 0V2H0.25V0H18.25ZM0.25 12V10H6.25V12H0.25ZM0.25 7V5H18.25V7H16.22C15.21 6.37 14.02 6 12.75 6C11.48 6 10.29 6.37 9.28 7H0.25Z"
                            fill="white">
                        </path>
                    </svg>
                </div>
                <a id="deals" class="button button--deals">Каталог</a>
            </div>

            <div class="intro__btn intro__home">
                <div class="intro__deals-icon">
                    <svg width="25" height="24" viewBox="0 0 25 24" fill="none" xmlns="http://www.w3.org/2000/svg"
                        style="flex-grow: 0; flex-shrink: 0; width: 24px; height: 24px; position: relative;"
                        preserveAspectRatio="xMidYMid meet">
                        <path d="M9.5 13H15.5V19H18.5V10L12.5 5.5L6.5 10V19H9.5V13ZM4.5 21V9L12.5 3L20.5 9V21H4.5Z"
                            fill="white"></path>
                    </svg>
                </div>
                <a id="deals" class="button button--deals">Главная</a>
            </div>
        </div>
    </div>
</template>

<style scoped></style>