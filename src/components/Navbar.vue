<!-- script -->
<script setup>
import { ref } from "vue";

const menuCounter = ref(false);
</script>
<!-- end script -->

<!-- template -->
<template>
  <nav
    class="@navbar z-10 fixed top-0 right-0 bg-white w-screen h-16 flex justify-between items-center p-2.5 shadow md:h-20 md:px-10"
  >
    <!-- logo and title -->
    <h1 class="font-semibold mt-1 text-2xl text-zinc-800">
      Simple <span class="text-[#7c5c36] font-['Grandstander']">Wiki</span>
    </h1>

    <!-- menu and search -->
    <div class="flex justify-center items-center gap-1.5">
      <a href="#" class="flex items-center justify-center w-[30px] h-[30px]">
        <!-- svg -->
        <svg
          viewBox="0 0 24 24"
          fill="hsl(217, 32.6%, 17.5%)"
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
        class="relative transition text-red-100 w-[30px] h-[30px]"
      >
        <!-- svg -->
        <svg
          viewBox="0 0 28 28"
          fill="hsl(217, 32.6%, 17.5%)"
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
      class="fixed top-0 right-0 z-20 h-screen transition-colors duration-300"
      :class="
        menuCounter ? 'w-[100vw] bg-[rgba(0,0,0,0.5)]' : 'w-0 bg-transparent'
      "
    >
      <section
        role="menu_list"
        class="@menu_list fixed top-0 right-0 h-screen transition-all duration-300 bg-white overflow-hidden"
        :class="menuCounter ? 'w-[80vw]' : 'w-0'"
      >
        <header class="w-full h-16 flex justify-end items-center p-2.5">
          <button
            @click="menuCounter = !menuCounter"
            class="w-[30px] h-[30px] text-xl flex justify-center items-center"
          >
            <i class="bi bi-box-arrow-right"></i>
          </button>
        </header>
        <section class="@list mx-4 border-b-2 overflow-hidden">
          <ul class="w-[100%] flex flex-col gap-1 pb-1 text-zinc-800">
            <li class="">
              <a href="#" class="block w-full p-2 rounded-md bg-amber-100"
                >Home</a
              >
            </li>
            <li class="">
              <a href="#" class="block w-full p-2 rounded-md bg-amber-100"
                >Search</a
              >
            </li>
            <li class="">
              <a href="#" class="block w-full p-2 rounded-md bg-amber-100"
                >About API</a
              >
            </li>
            <li class="">
              <a href="#" class="block w-full p-2 rounded-md bg-amber-100 underline text-blue-500"
                >API DOCUMENTATION (wikipedia)</a
              >
            </li>
            <li class="">
              <a href="#" class="block w-full p-2 rounded-md bg-amber-100"
                >Contact</a
              >
            </li>
          </ul>
        </section>
      </section>
    </div>
    <!-- menu list -->
  </nav>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->
