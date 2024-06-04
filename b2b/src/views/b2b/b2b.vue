<script setup>
import Header from "@/components/b2b/header/header.vue";
import Footer from "@/components/b2b/footer/footer.vue";
import ContactFormBlock from "@/components/b2b/contactForm/contact-form.vue";
import PartnersBlock from "@/components/b2b/ourPartners/partners.vue";
import BirazhaBlock from "@/components/b2b/birzha/birzha.vue";
import SocailBlock from "@/components/b2b/social/social.vue";
import ElectronBlock from "@/components/b2b/electron-torg/electronTorg.vue";
import B2bBlock from "@/components/b2b/b2b-block/b2b.vue";
import Intro from '@/components/b2b/intro/intro.vue';
</script>

<template>
    <Header />
    <Intro />
    <B2bBlock />
    <ElectronBlock />
    <SocailBlock />
    <BirazhaBlock />
    <PartnersBlock />
    <ContactFormBlock />
    <Footer />
</template>

<style scoped></style>