<script setup>
import { defineProps } from 'vue';
import arrhover from '@/assets/images/arrhover.svg';


const props = defineProps({
    image: String,
    title: String,
    link: String,
    description: String
});
</script>

<template>
    <a :href="props.link">
        <div class="card intro__card">
            <img class="arrhover" :src='arrhover' alt="arrhover" />
            
            <!-- Условие для отображения изображения -->
            <img v-if="props.image" :src="props.image" alt="Image" />
            <img v-else src="https://market.b2b-se.com/components/com_jshopping/files/img_products/b2b_se_logo_full_blue.png" alt="Default Image" />
            
            <h2 class="card__title">{{ props.title }}</h2>
            <p class="card__description">{{ props.description }}</p>
        </div>
    </a>
</template>