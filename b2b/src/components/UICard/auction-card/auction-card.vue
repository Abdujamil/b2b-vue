<script setup>
import './auction-card.scss'
import noImg from "@/assets/images/no-img.png"
</script>

<template>
    <a href="#" class="auction-card">
        <!-- <svg width="20" height="19" viewBox="0 0 20 19" fill="none" xmlns="http://www.w3.org/2000/svg"
            class="auction-card__favorite-icon">
            <path
                d="M10.1 15.55L10 15.65L9.89 15.55C5.14 11.24 2 8.39 2 5.5C2 3.5 3.5 2 5.5 2C7.04 2 8.54 3 9.07 4.36H10.93C11.46 3 12.96 2 14.5 2C16.5 2 18 3.5 18 5.5C18 8.39 14.86 11.24 10.1 15.55ZM14.5 0C12.76 0 11.09 0.81 10 2.08C8.91 0.81 7.24 0 5.5 0C2.42 0 0 2.41 0 5.5C0 9.27 3.4 12.36 8.55 17.03L10 18.35L11.45 17.03C16.6 12.36 20 9.27 20 5.5C20 2.41 17.58 0 14.5 0Z"
                fill="#D7E2F2"></path>
        </svg> -->
        <div class="auction-card__info">
            <div class="auction-card__img-block">
                <img class="auction-card__image" :src="noImg" alt="Auction Image" />
            </div>
            <div class="auction-card__body">
                <div class="auction-card__title">
                    <div class="auction-card__title-head">
                        <p class='auction-card__top-title'>Тендер</p>
                        <h2 class="auction-card__title-title">Заголовок тендера</h2>
                        <p class="auction-card__description">
                            Поставка Наборов для введения инсулина амбулаторных
                            Медтроник для медицинского применения, в пользу граждан...
                        </p>
                    </div>
                    <div class="auction-card__title-foot">
                        <a class="auction-card__btn">Москва</a>
                    </div>
                </div>
                <div class="auction-card__right-info">
                    <div class="auction-card__price">
                        <p class='auction-card__top-title'>Начальная цена</p>
                        <h2 class="auction-card__title-title">10 000 ₽</h2>
                    </div>
                    <div class="auction-card__publish">
                        <div class="auction-card__pub">
                            <p class='auction-card__top-title'>Опубликовано</p>
                            <h3>05.02.2024 в 16:01</h3>
                        </div>
                        <div class="auction-card__data-expired">
                            <p class='auction-card__top-title'>Истекает</p>
                            <h3>12.02.2024 в 16:01</h3>
                        </div>
                    </div>
                    <div class="auction-card__update">
                        <p class='auction-card__top-title'>Обновлено</p>
                        <h3>07.02.2024 в 12:37</h3>
                    </div>
                </div>
            </div>
        </div>
    </a>
</template>