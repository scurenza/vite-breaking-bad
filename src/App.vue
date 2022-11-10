<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppLoader from "./components/AppLoader.vue";

import CharacterList from "./components/CharacterList.vue";
import { store } from "./store"

export default {
  components: {
    AppHeader,
    AppLoader,
    CharacterList
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.store.loading = true;
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.store.characters = resp.data;
      console.log(this.store.characters);
    })
  }
}
</script>

<template>
  <div class="wrapper">
    <AppHeader />
    <main>
      <div class="container mt-3">
        <AppLoader v-if="!store.loading" />
        <CharacterList v-else />
      </div>
    </main>
  </div>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partials/variables" as *;

.wrapper{
  width: 100%;
  height: 100vh;
}
.container{
  background-color: $container-color;
  width: 75%;
  min-height: 150px;
}
</style>
