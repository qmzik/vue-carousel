<template>
  <div id="app">
    <h1 class="title">Vue carousel, swipe to the left or right</h1>
    <Carousel :images="images" />
  </div>
</template>

<script>
import Carousel from './components/Carousel.vue'

export default {
  name: 'app',
  components: {
    Carousel
  },
  data() {
    return {
      images: [
        { id: '1', name: 'dark', src: 'https://images.unsplash.com/photo-1572105701471-a050ae49f687?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80' },
        { id: '2', name: 'man', src: 'https://images.unsplash.com/photo-1429159865929-f0cea488cd10?ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80' },
        { id: '3', name: 'desert', src: 'https://images.unsplash.com/photo-1548778039-671727cc96a0?ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80' },
      ]
    }
  }
}
</script>

<style>
body, html {
  margin: 0;
  padding: 0;
}

.title {
  text-align: center;
  font-size: 50px;
}
</style>
