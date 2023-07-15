<script setup lang="ts">
import { ref, type Ref } from "vue";
import Loading from "@/views/loading.vue";

const TYPING_SPEED: number  = 100;
const TITLES: Array<string> = ["The name is DK"];

let title : Ref<string> = ref("");
let cursor: Ref<string> = ref("_");

let _ci: number = 0;
let _ti: number = 0;

let show_loading: Ref<boolean> = ref(false);

setTimeout(type_text, TYPING_SPEED);

function type_text(): void {
    title.value += TITLES[_ti][_ci++];
    console.log(title.value);
    if (title.value.length < TITLES[_ti].length) {
        setTimeout(type_text, TYPING_SPEED);
    } else {
        cursor.value = "";
        show_loading.value = true;
    };
}
</script>

<template>
<header>
    <h1>{{ title }}<span class="blinking-cursor">{{ cursor }}</span></h1>
    <hr>
    <Loading :show=show_loading />
</header>
</template>



<style scoped>
header {
    line-height: 1.5;
    max-height: 100vh;
    max-width: 100vw;
    text-align: center;
}

header h1 {
    font-weight: 900;
}

@media (min-width: 640px) {
    header h1 {
        font-size: 64px;
    }
}

header .blinking-cursor {
    font-weight: 900;
    animation: 0.5s blink step-end infinite
}

hr {
    margin-bottom: 16px;
    border-color: var(--color-border);
    border-radius: 8px;
    border-width: 1px;
}

@keyframes blink {
    from, to {
        color: transparent;
    }
    50% {
        color: inherit;
    }
}
</style>