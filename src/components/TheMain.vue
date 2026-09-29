<script setup>
import { ref } from 'vue';

const selectedIndex = ref(null);

const icons = [
    '🐉','🌿','🐚','🐍','🦜','🔥','🐴','⭐',
    '🐦','😈','🐛','🍡','🦇','🐵','👻','🐔',
    '🐸','🐢','🦋','🐝','🐞','🦀','🐙','🐠',
    '🦁','🐯','🐻','🐼','🐨','🦊','🐰','🦝',
    '🐺','🐗','🐮','🐷','🐭','🐹','🐿️','🦔',
    '🦉','🦅','🦢','🦩','🦚','🦆','🐋','🐬',
    '🦈','🐊','🦕','🦖','🐳','🦑','🦐','🦞',
    '🐌','🕷️','🦂','🪲','🪳','🦟','🪰','🐝'
];


function selectTile(index) {
    selectedIndex.value = selectedIndex.value === index ? null : index;
}
const tiles = ref([]);
for (let i = 0; i < 100; i++) {
    tiles.value.push(icons[i % icons.length]);
}
</script>

<template>
    <div class="board">
        <div class="cell" v-for="(icon, index) in tiles" @click="selectTile(index)" :key="index" :class="{ selected: selectedIndex === index }">
            {{ icon }}
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
</style>