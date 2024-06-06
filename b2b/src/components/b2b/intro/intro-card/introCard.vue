<script setup>
import { defineProps } from 'vue';
import arrhover from '@/assets/images/arrhover.svg';
import axios from 'axios';

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: '/api/index.php?option=com_jshopping&controller=addon_api&section=product&task=list&args[limit]=20',
  headers: { 
    'Authorization': 'Bearer RmIF677BiWxLCUI2ImckQQ7RqUGrDjcA', 
    'Cookie': '55e884495441419f79abfcee0eb88317=7eebfe30d9c231c6008e1ae54e071a5a'
  }
};

axios.request(config)
.then((response) => {
//   const data = response.data;
//   console.log(JSON.stringify(typeof(response.data)));
//   console.log(JSON.stringify(response.data[result]));
for (var res in response) {
    console.log(JSON.stringify(response[res]['result']['parent_id']));
}
})
.catch((error) => {
    console.error('Error:', error.response ? error.response.data : error.message);
});


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