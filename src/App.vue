<template>
  <div id="app">
    <LandingPage :inputFile="inputFile"/>
  </div>
</template>

<script>
/* eslint-disable no-alert, no-console */
import LandingPage from './components/LandingPage.vue'

export default {
  name: 'app',
  components: {
    LandingPage
  },
  data: function() {
    return {
      inputFile: "index.json",
      title: "Staging list"
    }
  },
  created () {
    if (this.title) {
      document.title = this.title;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height:100%;
  width: 100%;
  position:absolute;
}

body {
  margin: 0px;
}

.boundary {
  width:500px;
  height:500px;
  top:100px;
  left:100px;
  background-color:thistle;
  position: absolute;
}

</style>
