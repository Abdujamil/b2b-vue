<script setup>
import CardImg from "@/assets/images/no-img.png";
import Ava1 from '@/assets/images/ava1.png'
import './socialCard.scss';

</script>

<template>
    <div class="socials__card">
        <div class="socials__avatar">
            <img :src="Ava1" alt="avatar" class="socials__avatar-img" />
        </div>
        <div class="socials__about">
            <h3 class="socials__profession">Профессия</h3>
            <p class="socials__fio">
                Константинопольский Константин Константино...
            </p>
        </div>
    </div>

</template>
