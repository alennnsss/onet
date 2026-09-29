<template>
    <div class="body">
        <TheHeader />
        <TheMain />
    </div>
</template>

<script setup>
import TheHeader from '../components/TheHeader.vue';
import TheMain from '../components/TheMain.vue';
</script>

<style scoped>
    .body {
        background-color: black;
        padding: 10px 50px;
    }
</style>    