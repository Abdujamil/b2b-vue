<script setup>
import { ref } from 'vue';

import logo from '@/assets/images/logo.svg'
import search from '@/assets/images/search.svg';
import loginIcon from '@/assets/images/loginIcon.svg';
import favorites from '@/assets/images/favorites.svg';
import deals from '@/assets/images/deals.svg';
import catalogIcon from '@/assets/images/catalogIcon.svg';
import GreenBtn from '@/components/UIbuttons/greenBtn/greenButton.vue'
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue';
</script>

<template>
    <div class="intro">
        <div class="intro__container container">
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
                </div>
            </div>

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
                    <h1 class="home__slider-title">Что мы предлагаем?</h1>
                    <p class="home__slider-subtitle">Инструмент для решения каждодневных задач.</p>
                </div>
                <div class="swiper-container home__swiper">
                    <div class="swiper-wrapper home__swiper-wrapper">
                        <div class="swiper-slide home__slide">
                            <div class="card home__card">
                                <img :src="fulfilment" alt="fulfilment" class="card__image" />
                                <h2 class="card__title">Фулфилмент</h2>
                                <p class="card__description">Размещайте свои товары на наших складах</p>
                            </div>
                            <div class="card home__card">
                                <img :src="birzha" alt="birzha" class="card__image" />
                                <h2 class="card__title">Биржа грузоперевозок</h2>
                                <p class="card__description">Перевозка и доставка груза по России</p>
                            </div>
                        </div>
                        <div class="swiper-slide home__slide">
                            <div class="card home__card">
                                <img :src="b2b_market" alt="b2b_market" class="card__image" />
                                <h2 class="card__title">B2B Рынок</h2>
                                <p class="card__description">Купля / продажа товаров. Только для юридических лиц</p>
                            </div>
                            <div class="card home__card">
                                <img :src="dolly" alt="dolly" class="card__image" />
                                <h2 class="card__title">Биржа фриланса</h2>
                                <p class="card__description">Находите исполнителей и заказчиков. Безопасные сделки</p>
                            </div>
                        </div>
                    </div>
                    <div class="swiper-button-next home__swiper-button-next"></div>
                    <div class="swiper-button-prev home__swiper-button-prev"></div>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped></style>