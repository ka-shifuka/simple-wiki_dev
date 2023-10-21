<!-- script -->
<script setup>
  import { ref, onMounted } from "vue";

  const data = ref({});
  onMounted(() => {
    const searchBar = document.querySelector("#search_bar");
    searchBar.addEventListener("change", async () => {
      const url = `https://id.wikipedia.org/w/api.php?action=query&generator=search&gsrsearch=${searchBar.value}&exintro=&prop=extracts%7Cpageimages&format=json&origin=*`;

      const response = await fetch(url);
      const dataJson = await response.json();
      const query = [];
      for (let i in dataJson.query.pages) {
        query.push(dataJson.query.pages[i]);
      }
      // filtering query because some of the output does not match the query
      const filterQuery = query.filter(data => {
        const title = data.title.toLowerCase();
        return title.includes(searchBar.value.trim().toLowerCase());
      });

      if (filterQuery.length == 0) {
        data.value = query;
      } else {
        data.value = filterQuery.sort((a, b) => {
          var titleA = a.title.toUpperCase();
          var titleB = b.title.toUpperCase();
          if (titleA < titleB) {
            return -1;
          }
          if (titleA > titleB) {
            return 1;
          }
          return 0;
        });
      }

      console.log(data.value, query, dataJson);
    });
  });
</script>
<!-- end script -->

<!-- template -->
<template>
  <div class="mx-4 sm:mx-10 xl:mx-[15%] min-h-[100vh]">
    <section role="Search" class="">
      <div class="w-full h-20 flex justify-center items-center">
        <!-- form and input search -->
        <form
          class="text-sm"
          action="javascript:void(0)"
          method="get"
          accept-charset="utf-8"
        >
          <input class="border" type="text" name="search_bar" id="search_bar" />
          <button type="submit">behdh</button>
        </form>
        <!-- form and input search -->
      </div>
      <div class="">
        <div v-if="data" class="">
          <div v-for="i in data" class="my-5">
            <p v-html="i.extract"></p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->