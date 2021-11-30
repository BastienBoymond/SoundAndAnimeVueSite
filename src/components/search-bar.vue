<template>
    <input type="text" v-model="search" placeholder="Search..."  v-on:keyup.enter="ytb_request(search)">
    <div v-if="display">
        <iframe type="text/html" width="1" height="1"
      :src="'https://www.youtube.com/embed/' + video + '?autoplay=1&origin=http://localhost:8080/'"
      frameborder="0"></iframe>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    

    name: 'SearchBar',
    data() {
        return {
            search: '',
            video: '',
            api_key: 'YOUR API KEY',
            display: false,
        }
    },
    methods:
    {
        async ytb_request(search)
        {
            this.search = search;

            const responses = await axios.get('https://www.googleapis.com/youtube/v3/search?part=snippet&type=video&maxResults=10&q=' + this.search + '&key=' + this.api_key);
            this.video = responses.data.items[0].id.videoId
            this.display = true;
        }
    }
}
</script>

<style>

input {
    position: absolute;
    top: 3%;
    right: 3%;
    border: none;
    border-radius: 0;
    padding: 0 15px;
    font-size: 1.2em;
    font-weight: bold;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 20px;
}

</style>