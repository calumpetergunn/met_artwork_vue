<template>
  <div id="app">
    <h1>Collection at the Met</h1>
    <artworks-header title="Highlights from the Met"/>
    <artworks-header v-if="!artworks.length" title="Uno Momento Por Favor"/>

    <div class="main-container">
      <artworks-list :artworks="artworks"/>
      <artworks-detail :artwork="selectedArtwork" :artworksFavourite="artworksFavourite"/>
    </div>
    <div>
      <artworks-favourite v-if="artworks.length" :artworksFavourite="artworksFavourite"/>
    </div>
    <div>
      <artworks-graph :artworks="artworks"/>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import ArtworksList from './components/ArtworksList.vue'
import ArtworksDetail from './components/ArtworksDetail.vue'
import ArtworksFavourite from './components/ArtworksFavourite.vue'
import ArtworksHeader from './components/ArtworksHeader.vue'
import ArtworksGraph from './components/ArtworksGraph.vue'

export default {
  name: 'App',
  components: {
    "artworks-list": ArtworksList,
    "artworks-detail": ArtworksDetail,
    "artworks-favourite": ArtworksFavourite,
    "artworks-header": ArtworksHeader,
    "artworks-graph": ArtworksGraph
  },
  data () {
    return {
      artworks: [],
      selectedArtwork: null,
      artworksFavourite: [],
      artworksYears: []
    }
  },

  async mounted() {
    const promises = [438821, 438817, 436535, 435882, 751538, 12388, 10819, 18354, 11120, 20768, 13171, 5630, 751542, 6906, 435868, 436528, 436819, 436947, 634108, 435962, 436532, 437299, 437549, ].map(async (number) => {
      const response = await fetch(`https://collectionapi.metmuseum.org/public/collection/v1/objects/${number}`)
      return await response.json()
    })
    const nestedArtWorks = await Promise.all(promises)
    this.artworks = nestedArtWorks.flat()
    

    
    eventBus.$on('artwork-selected', (artwork) => {
      this.selectedArtwork = artwork;
    })

    eventBus.$on('artwork-added', (artwork) => {
      this.artworksFavourite.push(artwork);

    })



    // eventBus.$on('artwork-removed' (artwork) => {
    //   this.artworksFavourite.
    // })
  }

}
</script>

<style>
#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}

.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
