<!-- script -->
<script setup>
import Navbar from "./components/Navbar.vue";
import Jumbotron from "./components/Jumbotron.vue";
</script>
<!-- end script -->

<!-- template -->
<template>
  <div class="@container w-screen h-screen flex flex-col justify-between">
    <!-- main header page -->
    <section>
      <Navbar></Navbar>
      <Jumbotron></Jumbotron>
    </section>
    <!-- main header page -->

    <!-- fotter page -->
    <section>footer</section>
    <!-- fotter page -->
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->
