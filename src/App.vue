<template>
  <header class="text-white">
    <h1 class="text-4xl font-bold">IP Address Tracker</h1>
    <form @submit.prevent="handleSubmit" class="relative m-4 mb-8 w-11/12 md:w-6/12">
      <SearchBox
        v-model:value="domain"
        placeholder="Search for any IP address or domain"
        button-text=">"
      />
    </form>
  </header>
  <main class="relative">
    <DetailsBox v-bind:details="result" />
    <MapView v-bind:loc="result.location" />
  </main>
</template>

<script>
import { ref } from "vue";
import { ipifyKey } from "../.keys";
import DetailsBox from "./components/DetailsBox";
import MapView from "./components/MapView";
import SearchBox from "./components/SearchBox";

export default {
  name: "App",
  components: {
    DetailsBox,
    MapView,
    SearchBox,
  },
  setup() {
    const domain = ref("");
    const result = ref({});

    async function handleSubmit() {
      const response = await fetch(
        `https://geo.ipify.org/api/v1?apiKey=${ipifyKey}&domain=${domain.value}`
      );
      result.value = await response.json();
    }
    return { domain, handleSubmit, result };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap");
</style>
<style scoped>
header {
  background: center / cover no-repeat url(/pattern-bg.png);
  text-align: center;
  padding: 3em;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
