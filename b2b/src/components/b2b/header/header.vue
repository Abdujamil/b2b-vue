<script setup>
import { ref } from 'vue';
import Dropdown from 'primevue/dropdown';
import closeBtn from '@/assets/images/close.svg';
import burgerBtn from '@/assets/images/burger.svg';

const isOpenMenu = ref(false);

</script>

<template>
  <header class="header" ref="header">
    <img 
    :src='burgerBtn'
    @click="isOpenMenu ? true : false" 
    alt="burgeer" 
    class="header__btn header__open-btn"
    >
    <nav class="header__menu">
      <img :src='closeBtn' alt="close" class="header__btn header__close-btn">
      <ul class="menu">
        <li class="menu__item">
          <a class="menu__link" href="#">B2B Рынок</a>
        </li>
        <li class="menu__item">
          <a class="menu__link" href="#">Биржа грузоперевозок</a>
        </li>
        <li class="menu__item">
          <a class="menu__link" href="#">Тендеры / Аукционы</a>
        </li>
        <li class="menu__item">
          <a class="menu__link" href="#">Соцсеть</a>
        </li>
        <li class="menu__item">
          <a class="menu__link" href="#">Фриланс</a>
        </li>
        <li class="menu__item">
          <a class="menu__link menu__link-help" href="#">Помощь</a>
        </li>
        <li class="menu__item">
          <a class="menu__link" href="#">Тарифы</a>
        </li>
        <li class="menu__item menu__link-about" ref="aboutItem">
          <a class="menu__link menu__link-help" href="#">О нас</a>
        </li>
        <li class="menu__item dropdown">
          <a class="menu__link" href="#">Ещё</a>
          <ul class="submenu">
            <li><a class="submenu__link" href="#">Помощь</a></li>
            <li><a class="submenu__link" href="#">О нас</a></li>
            <li><a class="submenu__link" href="#">Контакты</a></li>
          </ul>
        </li>
      </ul>
      <a href="#" class="header__btn-join">Стать участником</a>
    </nav>
  </header>
</template>
<style scoped></style>