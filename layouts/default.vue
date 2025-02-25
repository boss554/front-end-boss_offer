<template>
    <HeadComponent/>
    <HeaderComponent/>
    <main>
        <slot/>
    </main>
    <FooterComponent/>
</template>


<script setup>
import FooterComponent from '@/components/footerComponent.vue';
import HeadComponent from '@/components/headComponent.vue';
import HeaderComponent from '@/components/headerComponent.vue';
import HomeComponent from '~/components/homeComponent.vue';
</script>