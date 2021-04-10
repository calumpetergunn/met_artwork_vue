<template>
  <section>
      <h2>Favourite Artworks</h2>
        <ul>
            <li v-for="artworkFavourite in artworksFavourite">
                {{artworkFavourite.title}}
            </li>
        </ul>
  </section>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: "artworks-favourite",
    props: ['artworksFavourite', 'artwork']

}
</script>

<style scoped>

</style>>

</style>