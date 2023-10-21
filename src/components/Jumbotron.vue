<!-- script -->
<script setup></script>
<!-- end script -->

<!-- template -->
<template>
  <div
    class="@container w-screen h-[100vh] bg-no-repeat bg-cover brightness-[.80] flex flex-col justify-center"
    style="background-image: url(&quot;/background.jpeg&quot;)"
  >
    <div
      class="mx-4 sm:mx-10 xl:mx-[15%] flex flex-col justify-center gap-5 sm:flex-row sm:justify-between"
    >
      <div class="sm:w-[300px] flex flex-col justify-center gap-4">
        <header class="">
          <h1 class="font-semibold mt-1 text-2xl text-zinc-100">
            Welcome to Simple
            <span class="text-yellow-500 font-['Grandstander']">Wiki</span>
          </h1>
          <p class="text-zinc-100 text-sm">
            simpel wiki adalah aplikasi pencarian sederhana yang terintregasi
            dengan
            <a
              href="https://github.com/mudroljub/wikipedia-api-docs"
              class="text-blue-400 underline"
              >API Wikipedia</a
            >
          </p>
        </header>
        <main>
          <div class="flex gap-2 text-zinc-800 font-semibold">
            <a href="" class="p-2 rounded-lg bg-yellow-500">Github</a>
            <a href="" class="p-2 rounded-lg bg-yellow-500">About creator</a>
          </div>
        </main>
      </div>

      <div
        class="hidden md:w-[200px] sm:flex sm:justify-center sm:items-center drop-shadow-2xl"
      >
        <img class="w-40 h-fit up-down" src="/books.png" alt="books" />
      </div>
    </div>
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