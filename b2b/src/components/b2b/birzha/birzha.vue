<script setup>
import { onMounted, ref } from "vue";
import CustomBtn from "../../UIbuttons/customBtn/customBtn.vue";
import CustomCard from "../../UICard/custom-card/customCard.vue";

// link
const birzhaLink = 'https://b2b-se.com/birzha-gruzoperevozok.html';

// Button change
const activeButton = ref('all');

function setActiveButton(button) {
    activeButton.value = button;
}
</script>



<template>
    <div class="birzha">
        <div class="birzha__container container">
            <div class="birzha__title">
                <h2 class="title">Биржа грузоперевозок</h2>
                <p class="subtitle">Перевозка и доставка груза по России.</p>
            </div>
            <div class="birzha-trading-btns">
                <button class="trade-btn all-category" :class="{ active: activeButton === 'all' }"
                    @click="setActiveButton('all')">
                    <svg width="25" height="24" viewBox="0 0 25 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M21.5 16.5C21.5 16.88 21.29 17.21 20.97 17.38L13.07 21.82C12.91 21.94 12.71 22 12.5 22C12.29 22 12.09 21.94 11.93 21.82L4.03 17.38C3.71 17.21 3.5 16.88 3.5 16.5V7.5C3.5 7.12 3.71 6.79 4.03 6.62L11.93 2.18C12.09 2.06 12.29 2 12.5 2C12.71 2 12.91 2.06 13.07 2.18L20.97 6.62C21.29 6.79 21.5 7.12 21.5 7.5V16.5ZM12.5 4.15L10.61 5.22L16.5 8.61L18.46 7.5L12.5 4.15ZM6.54 7.5L12.5 10.85L14.46 9.75L8.58 6.35L6.54 7.5ZM5.5 15.91L11.5 19.29V12.58L5.5 9.21V15.91ZM19.5 15.91V9.21L13.5 12.58V19.29L19.5 15.91Z"
                            fill="#00B066" />
                    </svg>

                    <span>Перевозчику</span><span>2.1K</span>
                </button>
                <div class="vertical-line"></div>
                <button class="trade-btn realty" :class="{ active: activeButton === 'realty' }"
                    @click="setActiveButton('realty')">
                    <svg width="25" height="24" viewBox="0 0 25 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M18.5 18.5C19.33 18.5 20 17.83 20 17C20 16.17 19.33 15.5 18.5 15.5C17.67 15.5 17 16.17 17 17C17 17.83 17.67 18.5 18.5 18.5ZM20 9.5H17.5V12H21.96L20 9.5ZM6.5 18.5C7.33 18.5 8 17.83 8 17C8 16.17 7.33 15.5 6.5 15.5C5.67 15.5 5 16.17 5 17C5 17.83 5.67 18.5 6.5 18.5ZM20.5 8L23.5 12V17H21.5C21.5 18.66 20.16 20 18.5 20C16.84 20 15.5 18.66 15.5 17H9.5C9.5 18.66 8.16 20 6.5 20C4.84 20 3.5 18.66 3.5 17H1.5V6C1.5 4.89 2.39 4 3.5 4H17.5V8H20.5ZM3.5 6V15H4.26C4.81 14.39 5.61 14 6.5 14C7.39 14 8.19 14.39 8.74 15H15.5V6H3.5Z"
                            fill="#00B066" />
                    </svg>
                    <span>Грузовладельцу</span><span>1.9K</span>
                </button>
            </div>
            <div class="b2b-cards">
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
                <CustomCard />
            </div>
            <CustomBtn :href="birzhaLink" />
        </div>
    </div>

</template>

<style scoped></style>