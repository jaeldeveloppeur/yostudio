<template>
  <div id="app">
    <welcome></welcome>
    <progress-circle-bar></progress-circle-bar>
  </div>
</template>

<script>
import ProgressCircleBar from './components/ProgressCircleBar.vue'
import Welcome from './components/Welcome.vue'

export default {
  name: 'App',
  components: {
    ProgressCircleBar,
    Welcome
  }
}
</script>

<style>
body{
    margin: 0;
    height: 4000px;
}

h1,h2,h3,h4,h5,h6{
  margin: 0;
}
</style>
