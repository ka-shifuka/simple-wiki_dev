<!-- script -->
<script setup>
  import { ref, onMounted } from "vue";
  const SESION_DATA = "SYSTME_THEME_QWERTY#1";

  const togglerCounter = ref(0); // 0 = light, 1 = dark, 2 = system
  const props = defineProps(["isDarkMode"]);

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
    props.isDarkMode(true);
    setSession(count);
  }
  function setLight(count) {
    clearInterval(interval);
    html.classList.remove("dark");
    togglerCounter.value = count;
    props.isDarkMode(false);
    setSession(count);
  }
  function setDefaultSys(count) {
    interval = setInterval(function () {
      if (
        window.matchMedia &&
        window.matchMedia("(prefers-color-scheme: dark)").matches
      ) {
        html.classList.add("dark");
        props.isDarkMode(true);
      } else {
        html.classList.remove("dark");
        props.isDarkMode(false);
      }
    }, 200);
    togglerCounter.value = count;
    setSession(count);
  }

  let isMounted = false; // This is to fix a bug where the name mounted is run 2 times instead of once
  onMounted(() => {
    if (!isMounted.value) {
      if (sessionStorage.getItem(SESION_DATA)) {
        const data = Number(sessionStorage.getItem(SESION_DATA));
        if (data === 0) setLight(0);
        if (data === 1) setDark(1);
        if (data === 2) setDefaultSys(2);
      }
      isMounted = true;
    }
  });
</script>
<!-- end script -->

<!-- template -->
<template>
  <div
    class="@ThemeToggler w-[30px] h-[30px] relative rounded shadow mx-2 transition-colors duration-300 active:bg-zinc-100 dark:bg-zinc-900 dark:active:bg-zinc-950 dark:text-zinc-100 cursor-pointer"
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
