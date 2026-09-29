<template>
    <header>
        <button @click="searchesMinus" class="attempt" :disabled="searchesLeft ===0">
            <img src="../assets/search-icon.png" alt="search" class="header-icon">
            <p>0 {{ searchesLeft }}</p>
        </button>
        <button @click="catchesMinus" class="attempt" :disabled="catchesLeft === 0">
            <img src="../assets/catched.png" alt="catched" class="header-icon">
            <p>0 {{ catchesLeft }}</p>
        </button>
        <div class="loader"></div>
        <p class="counter">0{{ counter }}</p>
    </header>
</template>

<script setup>
import { ref } from 'vue';

const searchesLeft = ref(7);
const catchesLeft = ref(7);
const counter = ref(0);

const searchesMinus = () => {
    searchesLeft.value -= 1;
}
const catchesMinus = () => {
    catchesLeft.value -=1;
}
</script>

<style scoped>
    header {
        padding-top: 20px;
        padding-bottom: 20px;
        display: flex;
        gap: 15px;
        height: 66px;
        justify-content: center;
    }
    .header-icon {
        background-color: skyblue;
        width: 24px;
        height: 24px;
        border-radius: 4px;
    }
    .attempt {
        border: none;
        display: flex;
        gap: 4px;
        background-color: black;
        align-items: center;

    }
    .attempt > p {
        color: white;
        font-weight: 900;
    }
    .loader {
        border: 2px solid yellow;
        background-color: green;
        width: 50%;
    }
    .counter {
        color: white;
        font-weight: 900;
        margin-top: 7px;
        margin-left: 50px;
    }
</style>