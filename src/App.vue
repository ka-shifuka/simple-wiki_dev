<!-- script -->
<script setup>
  import Navbar from "./components/Navbar.vue";
  import Jumbotron from "./components/Jumbotron.vue";
  import Search from "./components/Search.vue";
  import About from "./components/About.vue";
</script>
<!-- end script -->

<!-- template -->
<template>
  <div class="@container w-screen min-h-screen flex flex-col justify-between">
    <!-- main header page -->
    <div>
      <header>
        <Navbar></Navbar>
        <Jumbotron></Jumbotron>
      </header>
      <main>
        <Search></Search>
        <About></About>
      </main>
    </div>
    <!-- main header page -->

    <!-- fotter page -->
    <div class="bg-white">footer</div>
    <!-- fotter page -->
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->