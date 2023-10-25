<!-- script -->
<script setup></script>
<!-- end script -->

<!-- template -->
<template>
  <section
    id="about"
    class="@About relative top-[-5px] px-4 sm:px-10 xl:px-[10%] py-10 min-h-[500px] bg-white dark:bg-zinc-900"
  >
    <div class="flex flex-col justify-center items-center">
      <h1
        class="font-semibold text-3xl text-zinc-800 dark:text-zinc-300 tracking-wider"
      >
        About
      </h1>
      <h1 class="font-semibold mt-1 text-2xl text-zinc-800 dark:text-zinc-300">
        Simple
        <span class="text-yellow-700 font-['Grandstander']">Wiki</span>
      </h1>
    </div>
    <div class="flex flex-wrap justify-center items-center gap-5 my-5">
      <div
        class="w-[300px] h-[300px] bg-zinc-50 rounded-lg p-4 dark:bg-zinc-950"
      >
        <h1 class="font-semibold mt-1 text-lgtext-zinc-800 dark:text-zinc-300">
          Simple
          <span class="text-yellow-700 font-['Grandstander']">Wiki</span>
        </h1>
        <p
          class="text-zinc-700 text-[12px] tracking-tighter dark:text-zinc-400"
        >
          Adalah aplikasi open source yang dikembangkan sendiri oleh arya-mems
          sebagai project gabutnya. simple wiki adalah aplikasi pencari artikel
          sederhana yang terintegrasi dengan
          <a
            href="https://github.com/mudroljub/wikipedia-api-docs"
            class="text-blue-400 underline dark:brightness-75"
            >API Wikipedia.</a
          >
        </p>
      </div>

      <div
        class="w-[300px] h-[300px] bg-zinc-50 rounded-lg p-4 dark:bg-zinc-950"
      >
        <h1 class="font-semibold mt-1 text-md text-red-800">Warning!!!</h1>
        <p
          class="text-zinc-700 text-[12px] tracking-tighter dark:text-zinc-400"
        >
          Aplikasi ini masih memiliki bug berupa query yang terkadang aneh ini masih
          dalam tahap pengembanggan.
        </p>

        <div class="mt-5">
          <p
            class="text-zinc-700 text-[12px] tracking-tighter dark:text-zinc-400"
          >
            Tool dan alat pengembang lainya yang saya gunakan.
          </p>
          <ul
            class="px-5 text-zinc-600 text-[10px] list-disc dark:text-zinc-400"
          >
            <li class="">Acode (Code Editor)</li>
            <li class="">Termux + Nodejs (JavaScript runtime)</li>
            <li class="">Vue3 + Vite (Framework front-end)</li>
            <li class="">Bootstrap icon + svg repo (Icon dan svg)</li>
            <li class="">Tailwindcss (CSS framework)</li>
            <li class="">
              Wikipedia API (API untuk medapat data artikel dari Wikipedia)
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->