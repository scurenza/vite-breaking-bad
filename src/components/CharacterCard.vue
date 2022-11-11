<script>
export default {
    name: "CharacterCard",
    props: {
        character: Object
    }
}
</script>

<template>
    <div class="card-item text-center p-3">
        <img class="mb-3" :src="character.img" :alt="character.name">
        <h4 class="text-white fw-bold mb-4">{{ character.name }}</h4>
        <p class="text-secondary">{{ character.category }}</p>
        <p class="text-secondary">{{ character.status }}</p>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables" as *;
.card-item {
    background-color: $bg-color;
    min-height: 500px;
    
    p{
        margin: 0;
    }
}

</style>