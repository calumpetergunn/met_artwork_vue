<template>
  <section v-if="artwork">
    <h3>{{artwork.title}}</h3>
    <p>{{artwork.artistDisplayName}} - {{artwork.artistDisplayBio}}</p>
    <p>{{artwork.accessionYear}}</p>
    <p>{{artwork.medium}}</p>
    <button v-if="!artworksFavourite.includes(artwork)" @click="addToFavourites">Add to Favourites</button>
    <img :src="artwork.primaryImageSmall" alt="artwork Image">
    
  </section>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: "artworks-detail",
    props: ['artwork', 'artworks-favourite'],
    methods: {
        addToFavourites() {
            console.log(this.artwork)
            eventBus.$emit('artwork-added', this.artwork)
        }
    }
}
</script>

<style>

</style>