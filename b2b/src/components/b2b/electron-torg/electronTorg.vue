<script setup>
import { ref } from "vue";
import "./electronTorg.scss"
import CustomBtn from '@/components/UIbuttons/customBtn/customBtn.vue'
import AuctionCard from '@/components/UICard/auction-card/auction-card.vue'
// Button change
const activeButton = ref('all');

function setActiveButton(button) {
    activeButton.value = button;
}
</script>

<template>
    <div class="electronic-trading">
        <div class="electronic-trading__container container">
            <div class="electronic-trading__title">
                <h1 class="title">Электронные торги</h1>
                <p class="subtitle">
                    Выгодные закупки у лучших поставщиков. Быстрые и эффективные
                    продажи.
                </p>
            </div>
            <div class="electronic-trading__body">
                <div class="electronic-trading__btns">
                    <button 
                    class="trade-btn trade-btn--all-category" 
                    :class="{ active: activeButton === 'all' }"
                    @click="setActiveButton('all')"
                    >
                        <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M8 12C9.1 12 10 12.9 10 14C10 15.1 9.1 16 8 16C6.9 16 6 15.1 6 14C6 12.9 6.9 12 8 12ZM8 6C9.1 6 10 6.9 10 8C10 9.1 9.1 10 8 10C6.9 10 6 9.1 6 8C6 6.9 6.9 6 8 6ZM8 0C9.1 0 10 0.9 10 2C10 3.1 9.1 4 8 4C6.9 4 6 3.1 6 2C6 0.9 6.9 0 8 0ZM2 12C3.1 12 4 12.9 4 14C4 15.1 3.1 16 2 16C0.9 16 0 15.1 0 14C0 12.9 0.9 12 2 12ZM2 6C3.1 6 4 6.9 4 8C4 9.1 3.1 10 2 10C0.9 10 0 9.1 0 8C0 6.9 0.9 6 2 6ZM2 0C3.1 0 4 0.9 4 2C4 3.1 3.1 4 2 4C0.9 4 0 3.1 0 2C0 0.9 0.9 0 2 0ZM14 12C15.1 12 16 12.9 16 14C16 15.1 15.1 16 14 16C12.9 16 12 15.1 12 14C12 12.9 12.9 12 14 12ZM14 6C15.1 6 16 6.9 16 8C16 9.1 15.1 10 14 10C12.9 10 12 9.1 12 8C12 6.9 12.9 6 14 6ZM14 0C15.1 0 16 0.9 16 2C16 3.1 15.1 4 14 4C12.9 4 12 3.1 12 2C12 0.9 12.9 0 14 0Z"
                                fill="#00B066" />
                        </svg>
                        Все категории <span>2.1K</span>
                    </button>
                    <!-- <div class="electronic-trading__vertical-line"></div> -->

                    <button 
                    class="trade-btn trade-btn--realty" 
                    :class="{ active: activeButton === 'realty' }"
                    @click="setActiveButton('realty')"
                    >
                        <svg width="24" height="19" viewBox="0 0 24 19" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M10 0V2.26L12 3.59V2H22V17H17V19H24V0H10ZM7.5 3L0 8V19H15V8L7.5 3ZM14 4V4.93L15.61 6H16V4H14ZM18 4V6H20V4H18ZM7.5 5.5L13 9V17H10V11H5V17H2V9L7.5 5.5ZM18 8V10H20V8H18ZM18 12V14H20V12H18Z"
                                fill="#00B066" />
                        </svg>
                        Недвижимость
                        <span>201</span>
                    </button>
                    <!-- <div class="electronic-trading__vertical-line"></div> -->

                    <button 
                    class="trade-btn trade-btn--transport" 
                    :class="{ active: activeButton === 'transport' }"
                    @click="setActiveButton('transport')"
                    >
                        <svg width="19" height="16" viewBox="0 0 19 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M2.5 6L4 1.5H15L16.5 6H2.5ZM15 11C14.6022 11 14.2206 10.842 13.9393 10.5607C13.658 10.2794 13.5 9.89782 13.5 9.5C13.5 9.10218 13.658 8.72064 13.9393 8.43934C14.2206 8.15804 14.6022 8 15 8C15.3978 8 15.7794 8.15804 16.0607 8.43934C16.342 8.72064 16.5 9.10218 16.5 9.5C16.5 9.89782 16.342 10.2794 16.0607 10.5607C15.7794 10.842 15.3978 11 15 11ZM4 11C3.60218 11 3.22064 10.842 2.93934 10.5607C2.65804 10.2794 2.5 9.89782 2.5 9.5C2.5 9.10218 2.65804 8.72064 2.93934 8.43934C3.22064 8.15804 3.60218 8 4 8C4.39782 8 4.77936 8.15804 5.06066 8.43934C5.34196 8.72064 5.5 9.10218 5.5 9.5C5.5 9.89782 5.34196 10.2794 5.06066 10.5607C4.77936 10.842 4.39782 11 4 11ZM16.42 1C16.22 0.42 15.66 0 15 0H4C3.34 0 2.78 0.42 2.58 1L0.5 7V15C0.5 15.2652 0.605357 15.5196 0.792893 15.7071C0.98043 15.8946 1.23478 16 1.5 16H2.5C2.76522 16 3.01957 15.8946 3.20711 15.7071C3.39464 15.5196 3.5 15.2652 3.5 15V14H15.5V15C15.5 15.2652 15.6054 15.5196 15.7929 15.7071C15.9804 15.8946 16.2348 16 16.5 16H17.5C17.7652 16 18.0196 15.8946 18.2071 15.7071C18.3946 15.5196 18.5 15.2652 18.5 15V7L16.42 1Z"
                                fill="#00B066" />
                        </svg>
                        Транспорт
                        <span>1.9K</span>
                    </button>
                    <!-- <div class="electronic-trading__vertical-line"></div> -->

                    <button 
                    class="trade-btn trade-btn--land" 
                    :class="{ active: activeButton === 'land' }"
                    @click="setActiveButton('land')"
                    >
                        <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M17.5 0L17.34 0.03L12 2.1L6 0L0.36 1.9C0.15 1.97 0 2.15 0 2.38V17.5C0 17.6326 0.0526785 17.7598 0.146447 17.8536C0.240215 17.9473 0.367392 18 0.5 18L0.66 17.97L6 15.9L12 18L17.64 16.1C17.85 16.03 18 15.85 18 15.62V0.5C18 0.367392 17.9473 0.240215 17.8536 0.146447C17.7598 0.0526785 17.6326 0 17.5 0ZM7 2.47L11 3.87V15.53L7 14.13V2.47ZM2 3.46L5 2.45V14.15L2 15.31V3.46ZM16 14.54L13 15.55V3.86L16 2.7V14.54Z"
                                fill="#00B066" />
                        </svg>
                        Зем. участки
                        <span>10</span>
                    </button>
                </div>

                <div class="auctions-cards">
                   <AuctionCard />
                   <AuctionCard />
                   <AuctionCard />
                   <AuctionCard />
                </div>
            </div>
            <CustomBtn :href="birzhaLink" />
        </div>
    </div>
</template>


<style></style>