<script setup>
import { ref } from 'vue';
import Dropdown from 'primevue/dropdown';


</script>

<template>
  <header class="header" ref="header">
    <nav class="header__menu">
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
        <!-- <li class="dropdown">
          <a href="#">Ещё</a>
          <ul class="submenu">
            <li><a href="#">Помощь</a></li>
            <li><a href="#">О нас</a></li>
            <li><a href="#">Контакты</a></li>
          </ul>
        </li> -->
      </ul>
      <a href="#" class="header__btn-join">Стать участником</a>
    </nav>
  </header>
</template>
<style scoped></style>