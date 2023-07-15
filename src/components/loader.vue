<script setup lang="ts">
const props = defineProps<{
    loading: boolean
}>();

const circle_ids: number[] = [1, 2, 3];

</script>

<template>
    <div v-show="loading">
        <div
            v-for="circle_id in circle_ids" :key="circle_id"
            class="circle" :class="'id-'+circle_id.toString()"
        ></div>
    </div>
</template>

<style scoped>

.circle {
    width: 4px;
    height: 4px;
    margin: 4px;
    display: inline-block;
    border-radius: 100%;
    background-color: var(--color-text);
}
.circle.id-1 {
    animation: pulse 1s 0.12s infinite cubic-bezier(0.2, 0.68, 0.18, 1.08);
}

.circle.id-2 {
    animation: pulse 1s 0.24s infinite cubic-bezier(0.2, 0.68, 0.18, 1.08);
}

.circle.id-3 {
    animation: pulse 1s 0.36s infinite cubic-bezier(0.2, 0.68, 0.18, 1.08);
}

@keyframes pulse {
    0% { transform: scale(1); opacity: 1 }
    50%{ transform: scale(0.1); opacity: 0.7}
    100%{ transform: scale(1); opacity: 1 }
}

</style>