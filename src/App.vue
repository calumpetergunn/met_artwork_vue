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
    const promises = [840188, 840233, 840507, 841001, 841083, 841203, 841244, 841302, 841320, 841375, 841485, 841548, 841593, 841668, 841720, 842457, 842501, 842565, 842837, 842940, 842943, 842957, 843158, 843343, 843412, 843711, 843726, 843753, 843832, 844158].map(async (number) => {
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
