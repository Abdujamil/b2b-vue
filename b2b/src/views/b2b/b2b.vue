<script setup>
import Header from "@/components/b2b/header/header.vue";
import Footer from "@/components/b2b/footer/footer.vue";
import ContactForm from "@/components/b2b/contactForm/contact-form.vue";
import Partners from "@/components/b2b/ourPartners/partners.vue";
import Birazha from "@/components/b2b/birzha/birzha.vue";
import Socail from "@/components/b2b/social/social.vue";

import 'swiper/css';
import 'swiper/css/pagination';
import 'swiper/css/scrollbar';
</script>

<template>
    <Header />
    <Socail />
    <Birazha />
    <Partners />
    <ContactForm />
    <Footer />
</template>

<style scoped></style>