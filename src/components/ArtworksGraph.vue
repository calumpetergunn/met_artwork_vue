<template>
  <section>
     <GChart
     v-if=""
     />
  </section>
</template>

<script>
import {GChart} from 'vue-google-charts'
export default {
    name: 'artworks-graph',
    data() {
        return {
            chartOptions: {
                width: 800,
                height: 240,
                title: 'Chart data and that',
                colors: ['#084887', '#f58a07', '#f9ab55', '#f7f5fb', '#909cc2', '#C1BB8F', '#A176BC']
            }
        }
    },
    props: ['artworks'],
    components: {
        GChart
    }

}
</script>

<style>

</style>