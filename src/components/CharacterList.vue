<script>
import { store } from "../store";
import CharacterCard from "./CharacterCard.vue";

export default {
    name: "CharacterList",
    components: {
        CharacterCard
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="row row-cols-2 row-cols-md-4 g-3">
        <div class="col" v-for="character in store.characters" :key="character.char_id">
            <CharacterCard :character="character" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
</style>