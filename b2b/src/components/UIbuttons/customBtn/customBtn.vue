<script setup>
import { defineProps } from 'vue';
import "./customBtn.scss"

const props = defineProps({
    link: {
        type: String,
        default: ''
    }
});
</script>

<template>
    <div class="linkWrap">
        <a :href="link" class="link style-2">
          <span class="mask">
            <div class="link-container">
              <span class="link-title1 title-btn">Смотреть все -></span>
              <span class="link-title2 title-btn">Смотреть все -></span>
            </div>
          </span>
        </a>
      </div>
</template>

<style scoped></style>