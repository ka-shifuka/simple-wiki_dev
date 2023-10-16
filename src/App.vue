<!-- script -->
<script setup>
import Navbar from "./components/Navbar.vue";
import Jumbotron from "./components/Jumbotron.vue";
import { ref, onMounted } from "vue";

onMounted(() => {
  function isInViewPort(element) {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          console.log(entries, element);
        } else {
          console.log("no im ");
        }
      });
    });
    observer.observe(element);
  }

  setInterval(() => {
    const h = document.querySelector("#home");
    isInViewPort(h);
  }, 1000);
});
</script>
<!-- end script -->

<!-- template -->
<template>
  <div class="@container w-screen min-h-screen flex flex-col justify-between">
    <!-- main header page -->
    <section>
      <header>
        <Navbar></Navbar>
        <Jumbotron id="home"></Jumbotron>
      </header>
    </section>
    <!-- main header page -->

    <!-- fotter page -->
    <section class="h-[200vh]">footer</section>
    <!-- fotter page -->
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->
