<template>
  <section>
      <p @click="handleClick">{{artwork.title}} - {{artwork.artistDisplayName}}</p>

  </section>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: "artworks-item",
    props: ["artwork"],
    methods: {
      handleClick() {
        eventBus.$emit('artwork-selected', this.artwork)
      }
    }
}
</script>

<style scoped>

</style>