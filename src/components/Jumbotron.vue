<!-- script -->
<script setup>
  import { ref, onMounted } from "vue";

  onMounted(() => {
    const background = document.querySelector("#background-image");
    setInterval(() => {
      const count = Math.floor(window.scrollY / 5);
      background.style.transform = `translate(0, -${count}px)`;
      background.style.scale = 1 + count / 2000;
    }, 10);
  });
</script>
<!-- end script -->

<!-- 
    style="background-image: url(&quot;/background.jpeg&quot;)"
template -->
<template>
  <div
    id="home"
    class="@container relative w-screen h-[100vh] flex flex-col justify-center bg-fixed bg"
  >
    <!-- background-image -->
    <div
      id="background-image"
      class="w-screen h-[100vh] transition-all duration-[150ms] fixed bg-no-repeat bg-cover bg-center -z-[100]"
      style="
        background-image: linear-gradient(
            rgba(0, 0, 0, 0.3),
            rgba(0, 0, 0, 0.8)
          ),
          url(&quot;/background.jpeg&quot;);
      "
    ></div>
    <!-- background-image -->

    <!-- main -->
    <div
      class="mx-4 sm:mx-10 xl:mx-[10%] flex flex-col justify-center gap-5 sm:flex-row sm:justify-between"
    >
      <div class="sm:w-[300px] flex flex-col justify-center gap-4">
        <!-- header -->
        <header class="">
          <h1 class="font-semibold mt-1 text-2xl text-zinc-100">
            Welcome to Simple
            <span class="text-yellow-500 font-['Grandstander']">Wiki</span>
          </h1>
          <p class="text-zinc-200 text-[12px]">
            simpel wiki adalah aplikasi pencarian sederhana berbasis web yang
            sangat mudah digunakan yang terintregasi dengan
            <a
              href="https://github.com/mudroljub/wikipedia-api-docs"
              class="text-blue-400 underline"
              >API Wikipedia</a
            >
          </p>
        </header>
        <!-- header -->

        <!-- main -->
        <main>
          <div class="flex gap-2 text-zinc-800 font-semibold text-sm">
            <a href="" class="p-2 rounded-lg bg-yellow-500">Github</a>
          </div>
        </main>
        <!-- main -->
      </div>

      <!-- encathanted table -->
      <div
        class="hidden md:w-[200px] sm:flex sm:justify-center sm:items-center drop-shadow-2xl"
      >
        <img
          class="w-40 h-fit up-down drop-shadow-[0_35px_15px_rgba(0,0,0,0.5)]"
          src="/books.png"
          alt="books"
        />
      </div>
      <!-- encathanted table -->
    </div>
    <!-- main -->
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped>
  .up-down {
    animation: upDown 5s infinite;
  }

  @keyframes upDown {
    0% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-20px);
    }
    100% {
      transform: translateY(0);
    }
  }
</style>
<!-- end style -->