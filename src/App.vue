<!-- script -->
<script setup>
  import Navbar from "./components/Navbar.vue";
  import Jumbotron from "./components/Jumbotron.vue";
  import Search from "./components/Search.vue";
  import About from "./components/About.vue";
  import Contact from "./components/Contact.vue";
  import Footer from "./components/Footer.vue";
</script>
<!-- end script -->

<!-- template -->
<template>
  <div class="@App w-screen min-h-screen flex flex-col justify-between">
    <!-- main header page -->
    <div>
      <header>
        <Navbar></Navbar>
        <Jumbotron></Jumbotron>
      </header>
      <main>
        <Search></Search>
        <About></About>
        <Contact></Contact>
      </main>
    </div>
    <!-- main header page -->

    <!-- fotter page -->
    <div class="relative">
      <div
        class="w-full h-7 -z-20 absolute -top-6 bg-white dark:bg-zinc-900"
      ></div>
      <Footer></Footer>
    </div>
    <!-- fotter page -->
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->