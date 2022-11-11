<script>
import { store } from "../store";

export default {
    name: "AppSearch",
    data() {
        return {
            store,
            statusOption: ["Breaking Bad", "Better Call Saul"]
        }
    }
}
</script>

<template>
    <div class="d-flex justify-content-between shadow-none p-3 mb-5 rounded">
        <select class="form-select" name="Status" id="Status" v-model="store.searchStatus">
            <option selected value="">Select Section</option>
            <option v-for="(option, index) in statusOption" :value="option" :key="index">{{ option }}</option>
        </select>
        <div class="founded d-flex justify-content-center align-items-center text-white">
           {{ store.charactersNum }} characters found
        </div>
        <button class="btn btn-primary" @click="$emit('doSearch')">Search</button>
    </div>
</template>

<style lang="scss" scoped>
div{
    width: 60%;
    margin: 0 auto;
    border: 2px solid white;
    

    select{
        width: 40%;
    }

    .founded{
        width: 30%;
    }
}
</style>