<!-- script -->
<script setup>
  import { ref, onMounted } from "vue";

  const data = ref({});
  const isLoad = ref(false);
  const isNotValid = ref(false);

  onMounted(() => {
    const searchBar = document.querySelector("#search_bar");
    const errProp = document.querySelector("#error-property");
    // loading bar and error property
    searchBar.addEventListener("keyup", () => {
      isLoad.value = true;
      data.value = {};
    });
    setInterval(() => {
      if (searchBar.value === "") {
        errProp.classList.remove("hidden");
        isLoad.value = false;
        data.value = {};
        return;
      }
    }, 50);

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
          data.value = query.sort((a, b) => {
            var titleA = a.title.toUpperCase();
            var titleB = b.title.toUpperCase();
            if (titleA < titleB) return -1;
            if (titleA > titleB) return 1;
            return 0;
          });
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
        errProp.classList.add("hidden");
      } catch (err) {
        errProp.classList.remove("hidden");
      }
      isLoad.value = false;
    });
  });
</script>
<!-- end script -->

<!-- template -->
<template>
  <div
    class="@Search px-4 sm:px-10 xl:px-[10%] py-10 min-h-[500px] bg-white rounded-t-2xl dark:bg-zinc-900"
  >
    <div class="w-full h-20 flex justify-center items-center">
      <!-- form and input search -->
      <div class="text-sm relative flex items-center" id="search">
        <input
          class="border-2 border-zinc-200 p-2 w-[250px] rounded-lg focus:outline-none md:w-[500px] dark:bg-zinc-800 dark:text-zinc-300 dark:border-[hsl(240,15%,15.9%)]"
          type="search"
          id="search_bar"
          placeholder="Search something like 'arya'"
        />
        <i class="bi bi-search absolute right-3 text-zinc-400"></i>
        <p
          class="text-zinc-400 text-[8px] absolute bottom-[-18px] right-0 tracking-tighter dark:text-zinc-600"
        >
          !Tips jika query kurang sesuai ketik enter dua kali.
        </p>
      </div>
      <!-- form and input search -->
    </div>
    <div class="relative min-h-[300px]">
      <!-- load property -->
      <div
        v-if="isLoad"
        class="w-full h-full bg-white absolute z-10 top-0 left-0 flex justify-center items-center dark:bg-zinc-900"
      >
        <div
          class="w-20 h-20 rounded-full border-2 border-yellow-700 border-b-transparent animate-spin"
        ></div>
      </div>
      <!-- load property -->

      <!-- error property -->
      <div
        id="error-property"
        class="w-full h-[300px] flex justify-center items-center"
      >
        <h1 class="font-semibold text-zinc-400">Result Not Found</h1>
      </div>
      <!-- error property -->

      <!-- data view -->
      <div id="data-view">
        <div
          v-if="data"
          class="md:flex md:flex-wrap md:justify-evenly md:items-stretch md:gap-5"
        >
          <div
            v-for="i in data"
            class="my-5 rounded-lg bg-zinc-50 p-5 flex flex-col justify-between md:px-16 md:w-[700px] md:min-h-[100px] dark:bg-[hsl(240,3.7%,11.5%)] dark:text-zinc-300"
          >
            <div>
              <header class="flex justify-between mb-2">
                <p
                  v-if="isNotValid"
                  class="text-[10px] text-rose-800 md:text-[12px]"
                >
                  hasil mungkin tidak sesuai
                </p>
                <div></div>
                <p
                  v-if="!i.thumbnail"
                  class="text-[10px] text-rose-800 md:text-[12px]"
                >
                  tidak ada gambar!!
                </p>
              </header>
              <main>
                <div v-if="i.thumbnail" class="relative flex justify-center">
                  <img
                    class="relative my-2 rounded-lg bg-transparent md:scale-75"
                    :src="i.thumbnail.source"
                    alt="thumbnail"
                    loading="lazy"
                    fetchpriority="high"
                  />
                </div>
                <p
                  class="text-[12px] indent-2.5 md:text-[14px]"
                  v-html="i.extract"
                ></p>
              </main>
            </div>

            <div>
              <footer class="p-4 w-full h-10 flex justify-end">
                <a
                  class="text-blue-500 text-[10px] underline md:text-[12px]"
                  :href="`https://id.m.wikipedia.org/wiki/${i.title}`"
                  >lihat di wikipedia</a
                >
              </footer>
            </div>
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