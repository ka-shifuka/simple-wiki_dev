<!-- script -->
<script setup>
  import { ref, onMounted } from "vue";

  const data = ref({});
  const isNotValid = ref(false);
  const isLoad = ref(false);
  onMounted(() => {
    const searchBar = document.querySelector("#search_bar");
    searchBar.addEventListener("keyup", () => {
      setInterval(() => {
        if (searchBar.value === "") {
          isLoad.value = false;
          data.value = {};
          return;
        }
      }, 100);
      isLoad.value = true;
      data.value = {};
    });

    searchBar.addEventListener("keyup", async () => {
      try {
        const url = `https://id.wikipedia.org/w/api.php?action=query&generator=search&gsrsearch=${searchBar.value}&exintro=&prop=extracts%7Cpageimages&pithumbsize=1000&format=json&origin=*`;

        const response = await fetch(url);
        const dataJson = await response.json();
        const query = [];
        for (let i in dataJson.query.pages) {
          query.push(dataJson.query.pages[i]);
        }
        // filtering query because some of the output does not match the query
        const filterQuery = query.filter(data => {
          const title = data.title.toLowerCase();
          const includeTitle = title.includes(
            searchBar.value.trim().toLowerCase()
          );
          console.log(includeTitle);
          const isHavePre = data.extract.includes("<pre>");
          if (isHavePre) {
            data.extract = data.extract.split("<pre>");
          }
          isNotValid.value = false;
          return includeTitle;
        });

        if (filterQuery.length == 0) {
          data.value = query;
          isNotValid.value = true;
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
        console.log(filterQuery, query);
      } catch (err) {}

      isLoad.value = false;
    });
  });
</script>
<!-- end script -->

<!-- template -->
<template>
  <div class="mx-4 sm:mx-10 xl:mx-[15%] min-h-screen">
    <div class="w-full h-20 flex justify-center items-center">
      <!-- form and input search -->
      <form
        class="text-sm relative flex items-center"
        action="javascript:void(0)"
        method="get"
        accept-charset="utf-8"
      >
        <input
          class="border-2 p-2 w-[250px] rounded-lg focus:outline-none"
          type="text"
          name="search_bar"
          id="search_bar"
          placeholder="Search something like 'arya'"
        />
        <i
          @click="getData()"
          class="bi bi-search absolute right-3 text-zinc-400"
        ></i>
      </form>
      <!-- form and input search -->
    </div>
    <div class="relative w-[] min-h-[300px]">
      <!-- l'oad property -->
      <div
        v-if="isLoad"
        class="w-full h-full bg-white absolute z-10 top-0 left-0 flex justify-center items-center"
      >
        <div
          class="w-20 h-20 rounded-full border-2 border-yellow-700 border-b-white animate-spin"
        ></div>
      </div>

      <!-- load property -->

      <div v-if="data" class="">
        <div v-for="i in data" class="my-5 rounded bg-zinc-100 p-5">
          <header class="flex justify-between mb-2">
            <p v-if="isNotValid" class="text-[10px] text-rose-500">
              hasil mungkin tidak sesuai
            </p>
            <div></div>
            <p v-if="!i.thumbnail" class="text-[10px] text-rose-500">
              tidak ada gambar!!
            </p>
          </header>
          <main>
            <img
              class="my-2 rounded-lg"
              v-if="i.thumbnail"
              :src="i.thumbnail.source"
              alt="thumbnail"
              loading="lazy"
              fetchpriority="high"
            />
            <p class="text-[12px]" v-html="i.extract"></p>
          </main>
        </div>
      </div>
    </div>
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->