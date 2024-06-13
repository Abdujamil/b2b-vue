<script setup>
import { defineProps } from 'vue';
import arrhover from '@/assets/images/arrhover.svg';
import axios from 'axios';

// let config = {
//     method: 'get',
//     maxBodyLength: Infinity,
//     url: '/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=20',
//     headers: {
//         'Authorization': 'Bearer z8NQIIfEd882hvkP83WoOPJEqfCxMu42',
//         'Cookie': '55e884495441419f79abfcee0eb88317=050cb5ef2d9397eb2cd7dc471bc260c8'
//     }
// };

// axios.request(config)
// .then((response) => {
// for (var res in response) {
//     console.log(JSON.stringify(response.data['result']));
//     // console.log(JSON.stringify(response.data['result']['4']['name_ru-RU']));
//     // console.log(JSON.stringify(response.data['result']['4']['short_description_ru-RU']));
//     // console.log(JSON.stringify(response.data['result']['4']['product_price']));
//     // console.log(JSON.stringify(response.data['result']['4']['product_old_price']));
//     // console.log(JSON.stringify(response.data['result']['4']['image']));
// }
// })
// .catch((error) => {
//     console.error('Error:', error.response ? error.response.data : error.message);
// });


// axios
//     .request(config)
//     .then(response => console.log((response.data.result)))


// defineProps({
//     card: {
//         type: Object,
//         required: true
//     }
// });

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