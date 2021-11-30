<template>
  <div class="navbar">
    <a href="https://www.japscan.ws/"><img alt="Vue logo" src="./assets/japscan.png"></a>
    <search-bar></search-bar>
  </div>
  <music-search></music-search>
  <list></list>
</template>

<script>
import SearchBar from './components/search-bar.vue'
import List from './components/list.vue'


export default {
  name: 'App',
  components: {
    SearchBar,
    List,
  },
  data () {
    return {
      info: null,
      loading: true
    }
  },
  async mounted() {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

html {
  background: url(./assets/background.jpeg);
}

img {
  vertical-align: middle;
  width: 2%;
  height: auto;
}

search-bar {
  height: 100%;
  margin-top: 1%;
  margin-bottom: 1%;
}

.navbar {
  background-color: #212121 !important;
  border-bottom: 1px solid #e7e7e7;
  padding: 0 15px;
  height: 50px;
  line-height: 50px;
  font-size: 1.2em;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 20px;
}

</style>
