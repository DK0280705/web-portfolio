<script setup lang="ts">
import { ref, type Ref } from "vue";
import Loader from "@/components/loader.vue"

defineProps<{
    show: boolean,
}>()

const messages: string[] = ["The page will be loaded soon.", "What're you waiting for? this is a fake loading."]

let message_index: Ref<number> = ref(0);

setTimeout(() => { message_index.value = 1 }, 8000);

</script>

<template>
<div class="load-container" :class="{ shown: show }">
    <h4 style="margin-bottom: 8px;">{{ messages[message_index] }}</h4>
    <Loader :loading=true />
</div>
</template>

<style scoped>
.load-container {
    line-height: 1.5;
    height: 0vh;
    opacity: 0;
    transition: height 0.5s, opacity 1s;
}

.load-container.shown {
    height: 24px;
    opacity: 1;
}


</style>