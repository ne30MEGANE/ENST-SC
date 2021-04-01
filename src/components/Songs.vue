<template>
  <div class="songs_wrapper">
    <SongNav v-bind:musics="songs" />

    <div class="songs">
      <div class="list_wrapper">
        <div class="list" v-for="s in songs" v-bind:key="s.inner_id" v-bind:class="s.type">
          <div class="song_title">
            <h3>{{ s.title }}</h3>
          </div>
          <div class="song_info">
            <h6>Lv.{{ s.level }}</h6>
            <h6>{{ s.singer }}</h6>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SongNav from './Song-nav';

export default {
  name: "songs",
  components: { SongNav },
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

<style lang="scss" scoped>
@import "../stylesheets/variables";
@import "../stylesheets/song";

.songs{ // ランダム選曲モーダルでもsongクラスを適用
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  width: 100%;

  .list_wrapper{      
    background-color: $light_gray;
    border-radius: 3px;
    width: 90%;
    display: flex;
    flex-flow: row wrap;
    justify-content: space-around;

    &::after{ // 最後揃えるやつ
        content: "";
        display: block;
        width: 28%;
        height: 0;
        margin: 1%;
        padding: 11px;
    }
  }
}
</style>