<!-- script -->
<script setup>
  import Navbar from "./components/Navbar.vue";
  import Jumbotron from "./components/Jumbotron.vue";
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