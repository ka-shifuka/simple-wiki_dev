<!-- script -->
<script setup>
import { ref, onMounted } from "vue";

const togglerCounter = ref(0); // 0 = light, 1 = dark, 2 = system
const SESION_DATA = "SYSTME_THEME_QWERTY1#2";

onMounted(() => {
    if (sessionStorage.getItem(SESION_DATA)) {
        const data = Number(sessionStorage.getItem(SESION_DATA));
        if (data === 0) setLight(0);
        if (data === 1) setDark(1);
        if (data === 2) setDefaultSys(2);
        console.log(data, typeof data);
    }
});

//set data of Theme mode to sesionStorage
function setSession(data) {
    sessionStorage.setItem(SESION_DATA, data);
}

// theme system
const html = document.querySelector("html");
let interval = null;
function setDark(count) {
    clearInterval(interval);
    html.classList.add("dark");
    togglerCounter.value = count;
    setSession(count);
}
function setLight(count) {
    clearInterval(interval);
    html.classList.remove("dark");
    togglerCounter.value = count;
    setSession(count);
}
function setDefaultSys(count) {
    interval = setInterval(function () {
        if (
            window.matchMedia &&
            window.matchMedia("(prefers-color-scheme: dark)").matches
        ) {
            html.classList.add("dark");
        } else {
            html.classList.remove("dark");
        }
    }, 100);
    togglerCounter.value = count;
    setSession(count);
}
</script>
<!-- end script -->

<!-- template -->
<template>
    <div
        class="w-[30px] h-[30px] relative rounded shadow mx-2 transition-colors duration-300 active:bg-zinc-100"
    >
        <button
            @click="setDark(1)"
            v-if="togglerCounter === 0"
            class="_btn w-[30px] h-[30px] rounded"
        >
            <i class="bi bi-sun-fill"></i>
        </button>
        <button
            @click="setDefaultSys(2)"
            v-if="togglerCounter === 1"
            class="_btn w-[30px] h-[30px] rounded"
        >
            <i class="bi bi-moon-stars-fill"></i>
        </button>
        <button
            @click="setLight(0)"
            v-if="togglerCounter === 2"
            class="_btn w-[30px] h-[30px] rounded"
        >
            <i class="bi bi-tv-fill"></i>
        </button>
    </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped>
._btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>
<!-- end style -->
