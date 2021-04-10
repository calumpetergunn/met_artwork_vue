<template>
    <section>
        
        <artworks-item
        v-for="(artwork, index) in artworks"
        :artwork="artwork"
        :key="index"
        />

    </section>
</template>

<script>
import ArtworksItem from './ArtworksItem.vue'

export default {
    name: "artworks-list",
    props: ["artworks"],
    components: {
        "artworks-item": ArtworksItem
    }
}
</script>

<style scoped>
section {
    text-align: left;
}
</style>