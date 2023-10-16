<!-- script -->
<script setup>
import { ref, onMounted } from "vue";

const togglerCounter = ref(0); // 0 = light, 1 = dark, 2 = system

onMounted(() => {
  // Memeriksa jika tema gelap didukung oleh browser
  if (
    window.matchMedia &&
    window.matchMedia("(prefers-color-scheme: dark)").matches
  ) {
    console.log("Tema sistem: Gelap");
  } else {
    console.log("Tema sistem: Terang");
  }
});

// theme system
const html = document.querySelector("html");
let interval = null;
function setDark(count) {
  clearInterval(interval);
  html.classList.add("dark");
  togglerCounter.value = count;
}
function setLight(count) {
  clearInterval(interval);
  html.classList.remove("dark");
  togglerCounter.value = count;
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
      <i class="bi bi-sun"></i>
    </button>
    <button
      @click="setDefaultSys(2)"
      v-if="togglerCounter === 1"
      class="_btn w-[30px] h-[30px] rounded"
    >
      <i class="bi bi-moon-stars"></i>
    </button>
    <button
      @click="setLight(0)"
      v-if="togglerCounter === 2"
      class="_btn w-[30px] h-[30px] rounded"
    >
      <i class="bi bi-tv"></i>
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
