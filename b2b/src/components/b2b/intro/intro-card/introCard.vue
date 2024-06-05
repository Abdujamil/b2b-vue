<script setup>
import { defineProps } from 'vue';
import arrhover from '@/assets/images/arrhover.svg';


defineProps({
    image: String,
    title: String,
    description: String
})

</script>

<template>
    <div class="card intro__card">
        <img class="arrhover" :src='arrhover' alt="arrhover" />

        <img :src="image" alt="Image" v-if="image" />

        <h2 class="card__title">{{ title }}</h2>
        <p class="card__description">{{ description }}</p>
    </div>
</template>