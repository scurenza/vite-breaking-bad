<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppLoader from "./components/AppLoader.vue";
import AppSearch from "./components/AppSearch.vue";

import CharacterList from "./components/CharacterList.vue";
import { store } from "./store"

export default {
  components: {
    AppHeader,
    AppLoader,
    CharacterList,
    AppSearch
  },
  data() {
    return {
      store
    }
  },
  created() {
    // this.store.loading = true;
    // axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
    //   this.store.characters = resp.data;
    //   console.log(this.store.characters);
    // })

    this.getCharacters();
  },
  methods: {
    getCharacters () {
      this.store.loading = true;
      let apiUrl = "https://www.breakingbadapi.com/api/characters?category=";

      // OGGETTO PARAMS
      // let urlParams= "";
      if (this.store.searchStatus) {
        apiUrl += this.store.searchStatus;
      }

      axios.get(apiUrl)
      .then((resp) => {
        this.store.characters = resp.data;
        console.log(resp);
        this.store.charactersNum = resp.data.length;
      })
      .catch(error => {
        this.store.characters = [];
      })
      .finally(() => {
        this.store.loading = false;
      })
    }
  }
}
</script>

<template>
  <div class="wrapper">
    <AppHeader />
    <AppSearch @doSearch="getCharacters"/>
    <main>
      <div class="container mt-4 p-3">
        
        <AppLoader v-if="store.loading" />
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
  min-height: 170px;
}
</style>
