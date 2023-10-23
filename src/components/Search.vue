<!-- script -->
<script setup>
  import { ref, onMounted } from "vue";

  const data = ref({});
  const isNotValid = ref(false);
  const isLoad = ref(false);

  onMounted(() => {
    const searchBar = document.querySelector("#search_bar");
    // loading bar
    setInterval(() => {
      if (searchBar.value === "") {
        isLoad.value = false;
        data.value = {};
      }
    }, 100);
    searchBar.addEventListener("keyup", () => {
      isLoad.value = true;
      data.value = {};
    });

    // get data from wikipedia
    searchBar.addEventListener("keyup", async () => {
      try {
        const search = searchBar.value;
        const url = `https://id.wikipedia.org/w/api.php?action=query&generator=search&gsrsearch=${search}&exintro=&prop=extracts%7Cpageimages&pithumbsize=600&format=json&origin=*`;

        const response = await fetch(url);
        const dataJson = await response.json();
        const query = [];
        for (let i in dataJson.query.pages) {
          query.push(dataJson.query.pages[i]);
        }

        // filtering query because some of the output does not match the query
        const filterQuery = query.filter(data => {
          const title = data.title.toLowerCase();
          const includeTitle = title.includes(search.trim().toLowerCase());
          if (data.extract.includes("<pre>")) {
            data.extract = data.extract.split("<pre>");
          }
          isNotValid.value = false;
          return includeTitle;
        });

        //if the query filter is empty
        if (filterQuery.length == 0) {
          data.value = query;
          isNotValid.value = true;
        } else {
          data.value = filterQuery.sort((a, b) => {
            var titleA = a.title.toUpperCase();
            var titleB = b.title.toUpperCase();
            if (titleA < titleB) return -1;
            if (titleA > titleB) return 1;
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
  <div
    class="px-4 sm:px-10 xl:px-[10%] py-10 min-h-screen bg-white rounded-t-lg"
  >
    <div class="w-full h-20 flex justify-center items-center">
      <!-- form and input search -->
      <form
        class="text-sm relative flex items-center"
        action="javascript:void(0)"
        method="get"
        accept-charset="utf-8"
        id="search"
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

      <!-- data view -->
      <div id="data-view">
        <div
          v-if="data"
          class="md:flex md:flex-wrap md:justify-evenly md:items-stretch md:gap-5"
        >
          <div
            v-for="i in data"
            class="my-5 rounded-lg bg-zinc-50 p-5 md:w-[600px] md:max-h-[500px] md:overflow-scroll lg:w-[400px] xl:w-[500px]"
          >
            <header class="flex justify-between mb-2">
              <p v-if="isNotValid" class="text-[10px] text-rose-800">
                hasil mungkin tidak sesuai
              </p>
              <div></div>
              <p v-if="!i.thumbnail" class="text-[10px] text-rose-800">
                tidak ada gambar!!
              </p>
            </header>
            <main>
              <div v-if="i.thumbnail" class="relative flex justify-center">
                <img
                  class="relative my-2 rounded-lg bg-transparent"
                  :src="i.thumbnail.source"
                  alt="thumbnail"
                  loading="lazy"
                  fetchpriority="high"
                />
              </div>
              <p class="text-[12px]" v-html="i.extract"></p>
            </main>
          </div>
        </div>
      </div>
      <!-- data view -->
    </div>
  </div>
</template>
<!-- end template -->

<!-- style -->
<style scoped></style>
<!-- end style -->