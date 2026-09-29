<template>
    <Teleport to="body">
        <div v-if="isOpen" class="modal-overlay">
            <div class="modal-content">
                <header class="modal-header">
                    <slot name="header">
                        <h2></h2>
                    </slot>
                </header>
                <main class="modal-body">
                    <slot></slot>
                </main>
                <footer class="modal-footer">
                    <slot name="footer">
                        <button @click="emit('close')">Закрыть</button>
                    </slot>
                </footer>
            </div>
        </div>
    </Teleport>
</template>

<script setup>
defineProps({
    isOpen: Boolean
});

const emit = defineEmits(['close']);
</script>

<style scoped>
.modal-overlay {
    position: fixed;
    inset: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
}
.modal-content {
    background-color: white;
    padding: 20px;
    width: 400px;
    border-radius: 12px;
    max-height: 50vh;
    overflow: auto;
}
</style>