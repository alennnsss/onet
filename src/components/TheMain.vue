<script setup>
import { ref } from 'vue';

import Computer from '../assets/computer.png';
import Crossword from '../assets/crossword.png';
import BaseModal from './BaseModal.vue';
const modalOpen = ref(false);

function closeModal() {
    modalOpen.value = false;
}


function selectTile(index) {
    if (tiles.value[index].matched) return;

    if (selectedIndex.value === null) {
        selectedIndex.value = index;
        return;
    }

    const first = tiles.value[selectedIndex.value];
    const second = tiles.value[index];

    if (index !== selectedIndex.value && first.id === second.id) {
        first.matched = true;
        second.matched = true;
        coins.value++;
        winPrize(); 
    }

    selectedIndex.value = null;
}
const tiles = ref([]);
const selectedIndex = ref(null);
const coins = ref(0);
const icons = [
    {
        id: 1,
        image: Computer,
        name: 'Computer'
    },
    {
        id: 2,
        image: Crossword,
        name: 'Crossword'
    }
];
function winPrize() {
    if(coins.value === 30) {
        modalOpen.value = true
    }
}
for (let i = 0; i < 60; i++) {
    tiles.value.push({ ...icons[i % icons.length], matched: false });
}
</script>

<template>
    <div>
        <BaseModal :isOpen="modalOpen" @close="closeModal">
            <template #header>
                <h2>
                    You win!!!
                </h2>
            </template>
            <template #default>
                <p>Play again</p>
            </template>
        </BaseModal>    
        <div class="coins">Коины: {{ coins }}</div>
        <div class="board">
            <div
                class="cell"
                v-for="(tile, index) in tiles"
                :key="index"
                :class="{ selected: selectedIndex === index, matched: tile.matched }"
                @click="selectTile(index)"
            >
                <img :src="tile.image" draggable="false" />
            </div>
        </div>
    </div>    
</template>

<style scoped>
.board {
    display: flex;
    flex-wrap: wrap;
    width: 70%;
    margin: 0 auto;
}

.cell {
    width: 48px;
    height: 48px;
    background: lightgreen;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    cursor: pointer;
    border: 1px solid black;

}
.cell:hover {
    background: rgb(108, 178, 108);
}
.cell.selected,
.cell.selected:hover {
    background: rgb(3, 102, 3);
}
.coins {
    color: white;
}
.cell.matched {
    visibility: hidden;
}
</style>