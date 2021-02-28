<template>
  <div class="songs">
    <h3>songs</h3>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "songs",
  data() {
    return {
      songs: [],
      api_url: process.env.VUE_APP_MUSIC_API_URL,
      orders: "?orders=inner_id",
      loaded: false
    };
  },
  mounted() {
    axios.get( this.api_url + this.orders , {
      headers: { "X-API-KEY": process.env.VUE_APP_MUSIC_API_KEY },
      params: { limit: 500 }
    }).then((response) => {
      console.log(response)
      this.songs = response.data.contents;
      this.loaded = true; // 読み込み終わったらture
    });
  }
}

</script>