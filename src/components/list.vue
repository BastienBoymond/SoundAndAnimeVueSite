<template>
    <div class="loading" v-if="loading">Chargement...</div>

  <div class="card" v-else v-for="data in info" :key="data.id">
    <img :src="data.attributes.posterImage.medium" alt="poster">
    <div>{{ data.attributes.slug }}</div>
    <button>Voir la fiche</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'list',
    data () {
    return {
      info: null,
      loading: true
    }
    },
    async mounted() {
        this.info = await axios.get('https://kitsu.io/api/edge/anime?filter[categories]=adventure')
        this.loading = false
        this.info = this.info.data.data
        console.log(this.info)
        console.log('mounted')
    }
}
</script>

<style>

button {
  background-color: black;
  border: none;
  margin-top: 1%;
  color: white;
  padding: 15px 32px;
  text-align: center;
}

.card {
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  text-align: center;
}

.loading {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.5em;
    font-weight: bold;
    color: #2c3e50;
}

</style>