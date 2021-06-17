<template>
  <div class="songs_wrapper">
    <SongNav v-bind:musics="songs" @SortFilter="SortFilter"/>

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
      order: "?orders=inner_id", // 初期値
      query: "", // 初期値
      loaded: false
    };
  },
  mounted() {
    this.DataLoad();
  },
  methods: {
    DataLoad() {
      axios.get( this.api_url + this.order + this.query , {
        headers: { "X-API-KEY": process.env.VUE_APP_MUSIC_API_KEY },
        params: { limit: 500 }
      }).then((response) => {
        console.log(response)
        this.songs = response.data.contents;
      });
    },
    SortFilter(s) {
      this.order = s;
      this.DataLoad();
    }
  }
}

</script>

<style lang="scss" scoped>
@import "../stylesheets/variables";
::v-deep .songs{ // ランダム選曲モーダルでもsongクラスを適用
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

  .list{
    &::before{
      content: "";
      width: 0;
      height: 0;
      top: 0;
      left: 0;
      z-index: 1;
      position: absolute;
      border-style: solid;
      border-width: 50px 50px 0 0;
      border-top-color: inherit;
      border-right-color: transparent;
      border-bottom-color: transparent;
      border-left-color: transparent;
    }
    margin: 1%;
    padding: 11px;
    position: relative;
    width: 28%;
    background-color: white;
    display: flex;
    flex-flow: column nowrap;
    justify-content: space-around;

    .song_title{
      h3{
        position: relative;
        margin-left: 10%;
        margin-bottom: 4%;
        font-weight: bold;
        font-size: 18pt;
        color: inherit;
        border-bottom: 2px solid $light_gray;
        z-index: 4;
      }
      vertical-align: middle;
    }

    .song_info{
      display: flex;
      flex-flow: row nowrap;
      justify-content: space-between;
      align-items: center;
      padding-left: 10%;
      h6{
        margin: 0;
        font-weight: bold;
        font-size: 13pt;
      }
    }
  }
  }
}
</style>