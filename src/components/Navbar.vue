<!-- script -->
<script setup>
  import ThemeToggler from "./ThemeToggler.vue";
  import { ref } from "vue";

  const menuCounter = ref(false);
  const elementInViewPort = ref(0); // 0 = home, 1 = about
  const isDarkMode = ref(false);

  function setDarkMode(value) {
    isDarkMode.value = value;
  }
</script>
<!-- end script -->

<!-- template -->
<template>
  <nav
    class="@Navbar z-50 fixed top-0 right-0 bg-white w-screen h-16 flex justify-between items-center p-2.5 shadow transition-colors duration-300 sm:h-20 sm:px-10 dark:bg-zinc-800 xl:px-[10%]"
  >
    <!-- logo and title -->
    <h1 class="font-semibold mt-1 text-2xl text-zinc-800 dark:text-zinc-200">
      Simple
      <span class="text-yellow-700 font-['Grandstander']">Wiki</span>
    </h1>
    <!-- logo and title -->
    <div class="hidden xl:block"></div>
    <div class="hidden lg:block"></div>
    <div class="hidden lg:block"></div>

    <!-- menu list in md screen -->
    <section role="menu_list" class="hidden md:block">
      <ul class="flex gap-2 text-sm dark:text-zinc-200">
        <li class="">
          <a
            href="#home"
            class="cursor-pointer transition-colors duration-300 p-1 rounded hover:text-zinc-600 dark:hover:text-zinc-400"
            >Home</a
          >
        </li>
        <li class="">
          <a
            href="#about"
            class="cursor-pointer transition-colors duration-300 p-1 rounded hover:text-zinc-600 dark:hover:text-zinc-400"
            >About</a
          >
        </li>
        <li class="">
          <a
            href="#contact"
            class="cursor-pointer transition-colors duration-300 p-1 rounded hover:text-zinc-600 dark:hover:text-zinc-400"
            >Contact</a
          >
        </li>
      </ul>
    </section>
    <!-- menu list in md screen -->

    <!-- menu and search -->
    <div class="flex justify-center items-center gap-1.5">
      <a
        href="#search"
        class="flex items-center justify-center w-[30px] h-[30px] cursor-pointer"
      >
        <!-- svg -->
        <svg
          viewBox="0 0 24 24"
          :fill="!isDarkMode ? 'hsl(217, 32.6%, 17.5%)' : 'hsl(240, 5.9%, 90%)'"
          xmlns="http://www.w3.org/2000/svg"
        >
          <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
          <g
            id="SVGRepo_tracerCarrier"
            stroke-linecap="round"
            stroke-linejoin="round"
          ></g>
          <g id="SVGRepo_iconCarrier">
            <rect width="24" height="24" fill="transparent"></rect>
            <path
              d="M7.25007 2.38782C8.54878 2.0992 10.1243 2 12 2C13.8757 2 15.4512 2.0992 16.7499 2.38782C18.06 2.67897 19.1488 3.176 19.9864 4.01358C20.824 4.85116 21.321 5.94002 21.6122 7.25007C21.9008 8.54878 22 10.1243 22 12C22 13.8757 21.9008 15.4512 21.6122 16.7499C21.321 18.06 20.824 19.1488 19.9864 19.9864C19.1488 20.824 18.06 21.321 16.7499 21.6122C15.4512 21.9008 13.8757 22 12 22C10.1243 22 8.54878 21.9008 7.25007 21.6122C5.94002 21.321 4.85116 20.824 4.01358 19.9864C3.176 19.1488 2.67897 18.06 2.38782 16.7499C2.0992 15.4512 2 13.8757 2 12C2 10.1243 2.0992 8.54878 2.38782 7.25007C2.67897 5.94002 3.176 4.85116 4.01358 4.01358C4.85116 3.176 5.94002 2.67897 7.25007 2.38782ZM9 11.5C9 10.1193 10.1193 9 11.5 9C12.8807 9 14 10.1193 14 11.5C14 12.8807 12.8807 14 11.5 14C10.1193 14 9 12.8807 9 11.5ZM11.5 7C9.01472 7 7 9.01472 7 11.5C7 13.9853 9.01472 16 11.5 16C12.3805 16 13.202 15.7471 13.8957 15.31L15.2929 16.7071C15.6834 17.0976 16.3166 17.0976 16.7071 16.7071C17.0976 16.3166 17.0976 15.6834 16.7071 15.2929L15.31 13.8957C15.7471 13.202 16 12.3805 16 11.5C16 9.01472 13.9853 7 11.5 7Z"
            ></path>
          </g>
        </svg>
        <!-- svg -->
      </a>

      <button
        @click="menuCounter = !menuCounter"
        class="relative transition text-red-100 w-[30px] h-[30px] cursor-pointer"
      >
        <!-- svg -->
        <svg
          viewBox="0 0 28 28"
          :fill="!isDarkMode ? 'hsl(217, 32.6%, 17.5%)' : 'hsl(240, 5.9%, 90%)'"
          xmlns="http://www.w3.org/2000/svg"
          transform="rotate(180)"
        >
          <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
          <g
            id="SVGRepo_tracerCarrier"
            stroke-linecap="round"
            stroke-linejoin="round"
          ></g>
          <g id="SVGRepo_iconCarrier">
            <path
              d="M4 7C4 6.44771 4.44772 6 5 6H24C24.5523 6 25 6.44771 25 7C25 7.55229 24.5523 8 24 8H5C4.44772 8 4 7.55229 4 7Z"
            ></path>
            <path
              d="M4 13.9998C4 13.4475 4.44772 12.9997 5 12.9997L16 13C16.5523 13 17 13.4477 17 14C17 14.5523 16.5523 15 16 15L5 14.9998C4.44772 14.9998 4 14.552 4 13.9998Z"
            ></path>
            <path
              d="M5 19.9998C4.44772 19.9998 4 20.4475 4 20.9998C4 21.552 4.44772 21.9997 5 21.9997H22C22.5523 21.9997 23 21.552 23 20.9998C23 20.4475 22.5523 19.9998 22 19.9998H5Z"
            ></path>
          </g>
        </svg>
        <!-- svg -->
      </button>
    </div>
    <!-- menu and search -->

    <!-- menu list -->
    <div
      class="fixed top-0 right-0 z-20 h-screen transition-colors duration-300 flex flex-1 cursor-pointer"
      :class="menuCounter ? '_in' : '_out'"
      @click="menuCounter = !menuCounter"
    >
      <div class="w-full bg-transparent"></div>
      <section
        role="menu_list"
        class="@menu_list fixed top-0 right-0 h-screen transition-all duration-300 bg-white overflow-hidden md:absolute md:right-10 md:top-16 md:rounded-lg md:flex md:flex-row-reverse md:justify-between md:items-center md:relative xl:right-[10%] dark:bg-zinc-800"
        :class="
          menuCounter ? 'w-[80vw] md:w-[300px] md:h-[100px]' : 'w-0 md:h-[0]'
        "
      >
        <header
          class="w-full h-16 flex justify-between items-center p-2.5 md:w-fit md:justify-end"
        >
          <ThemeToggler :is-dark-mode="setDarkMode"></ThemeToggler>
          <button
            @click="menuCounter = !menuCounter"
            class="w-[30px] h-[30px] text-xl flex justify-center items-center cursor-pointer md:absolute md:top-1 md:right-1 dark:text-zinc-200"
          >
            <i class="bi bi-box-arrow-right md:hidden"></i>
            <i class="bi bi-x hidden md:block"></i>
          </button>
        </header>
        <section class="@list mx-4 overflow-hidden md:hidden">
          <ul
            class="w-[100%] flex flex-col gap-1 pb-1 text-zinc-800 text-[12px] dark:text-zinc-200"
          >
            <li class="">
              <a
                href="#home"
                class="cursor-pointer block w-full p-2 rounded-md bg-zinc-100 cursor-pointer transition-colors duration-300 dark:bg-zinc-950"
                @click="menuCounter = !menuCounter"
                >Home</a
              >
            </li>
            <li class="">
              <a
                href="#search"
                class="cursor-pointer block w-full p-2 rounded-md bg-zinc-50 cursor-pointer transition-colors duration-300 dark:bg-zinc-900"
                @click="menuCounter = !menuCounter"
                >Search</a
              >
            </li>
            <li class="">
              <a
                href="#about"
                class="cursor-pointer block w-full p-2 rounded-md bg-zinc-50 cursor-pointer transition-colors duration-300 dark:bg-zinc-900"
                @click="menuCounter = !menuCounter"
                >About</a
              >
            </li>
            <li class="">
              <a
                href="#contact"
                class="cursor-pointer block w-full p-2 rounded-md bg-zinc-50 transition-colors duration-300 cursor-pointer dark:bg-zinc-900"
                @click="menuCounter = !menuCounter"
                >Contact</a
              >
            </li>
          </ul>
        </section>

        <!-- sosmed list -->
        <section
          role="sosmed_list "
          class="w-fit h-10 p-4 flex justify-end items-center gap-1.5 text-xl md:text-2xl md:gap-2 md:px-2.5"
        >
          <a
            href="https://www.facebook.com/profile.php?id=100072780309432&mibextid=ZbWKwL"
            class="bg-gradient-to-b from-blue-600 to-sky-600 bg-clip-text text-transparent cursor-pointer"
          >
            <i class="bi bi-facebook"></i>
          </a>
          <a
            href="https://instagram.com/arya_memes_dev?igshid=OGQ5ZDc2ODk2ZA=="
            class="bg bg-gradient-to-tr from-blue-600 to-pink-600 bg-clip-text text-transparent cursor-pointer"
          >
            <i class="bi bi-instagram"></i>
          </a>
          <a
            href="https://github.com/ka-shifuka"
            class="bg-gradient-to-b from bg-zinc-800 to-black bg-clip-text text-transparent cursor-pointer dark:from-zinc-200 dark:to-zinc-300"
          >
            <i class="bi bi-github"></i>
          </a>
        </section>
        <!-- sosmed list -->

        <!-- encathing table -->
        <div class="h-[50%] flex justify-center items-center md:hidden">
          <img
            class="w-32 h-32 up-down drop-shadow-[0px_35px_10px_rgba(0,0,0,0.3)]"
            src="/books.png"
          />
        </div>
      </section>
    </div>
    <!-- menu list -->
  </nav>
</template>
<!-- end template -->

<!-- style -->
<style scoped>
  ._in {
    animation-name: in;
    animation-duration: 400ms;
    animation-fill-mode: forwards;
    animation-timing-function: ease;
  }
  ._out {
    animation-name: out;
    animation-duration: 400ms;
    animation-fill-mode: forwards;
    animation-timing-function: ease;
  }

  @keyframes in {
    0% {
      width: 100vw;
    }
    50% {
      width: 100vw;
      background-color: rgba(0, 0, 0, 0.5);
    }
    100% {
      width: 100vw;
      background-color: rgba(0, 0, 0, 0.5);
    }
  }
  @keyframes out {
    0% {
      width: 100vw;
      background-color: rgba(0, 0, 0, 0.5);
    }
    99% {
      width: 100vw;
    }
    100% {
      width: 0vw;
    }
  }

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