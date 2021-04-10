<template>
  <div id="app">
    <p>Welcome!</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
  },
  data () {
    return {
      artworksList: []
    }
  },

  async mounted() {
    const promises = [500955, 500956, 500957, 500958, 500959, 500960, 500961, 500962, 500963, 500964, 500965, 500967, 500968, 500967, 500968, 500969, 500970, 500971, 500972, 500973, 500974, 500975, 500976, 500977, 500978, 500979, 500980, 500981, 500982, 500983, 500984].map(async (number) => {
      const response = await fetch(`https://collectionapi.metmuseum.org/public/collection/v1/objects/${number}`)
      return await response.json()
    })
    const nestedArtWorks = await Promise.all(promises)
    this.artworksList = nestedArtWorks.flat()
    console.log(this.artworksList)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
