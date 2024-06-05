<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import closeBtn from '@/assets/images/close.svg';
import burgerBtn from '@/assets/images/burger.svg';

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const handleResize = () => {
  const header = document.querySelector('.header');
  if (window.innerWidth <= 768) {
    header.style.display = 'none';
  } else {
    header.style.display = 'block';
  }
};

onMounted(() => {
  handleResize();
  window.addEventListener('resize', handleResize);
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleResize);
});
</script>


<template>
  <div>
    <header class="header">
      <img 
        :src="burgerBtn" 
        @click="toggleMenu" 
        alt="burger" 
        class="header__btn header__open-btn"
        v-if="isMenuOpen"
      >
      <nav class="header__menu" v-if="!isMenuOpen">
        <img 
          :src="closeBtn" 
          @click="toggleMenu" 
          alt="close" 
          class="header__btn header__close-btn"
        >
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
  </div>
</template>


<style>
.header--hidden {
  display: none;
}

.header__btn {
  cursor: pointer;
}
</style>