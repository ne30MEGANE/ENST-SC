<template>
  <div class="song_nav">
    <div class="navs">
      <p><a>フィルター・ソート</a></p>
      <p><a v-on:click="RandomModalOpen">ランダム選曲</a></p>
    </div>

    <!-- 以下モーダル -->
    <modal name="Random" height="auto" :maxWidth=595 styles="
      background: #e1e1e1;
      border: 2px solid #05034f;
      border-radius: 9px;">
      <h2 class="modal_title">ランダム選曲結果</h2>
      <div class="modal_body">
        <div class="list" v-bind:class="random_music.type" style="width:90%; margin:0 auto;">
          <div class="song_title">
            <h3>{{ random_music.title }}</h3>
          </div>
          <div class="song_info">
            <h6>Lv.{{ random_music.level }}</h6>
            <h6>{{ random_music.singer }}</h6>
          </div>
        </div>
        <div class="button_area">
            <p v-on:click="RandomModalClose" class="modal_button">閉じる</p>
        </div>
      </div>
    </modal>

  </div>
</template>

<script>

export default {
  name: "song-nav",
  props: ["musics"],
  data(){
    return {
      random_music: {
        "type": "",
        "title": "",
        "singer": "",
        "level": 0
      }
    }
  },
  methods: {
    SetRandomMusic: function(){ //ランダム選曲処理 (songsから1つ選んでセット)
      let i = getRandomInt(0, this.musics.length);
      this.random_music.type = this.musics[i].type;
      this.random_music.title = this.musics[i].title;
      this.random_music.singer = this.musics[i].singer;
      this.random_music.level = this.musics[i].level;
    },
    RandomModalOpen: function(){
      this.SetRandomMusic();
      this.$modal.show("Random");
    },
    RandomModalClose: function(){
      this.$modal.hide("Random");
    }
  }
}

function getRandomInt(min, max) { // 指定範囲内のランダムな整数を返す
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min;
}
</script>

<style lang="scss" scoped>
@import "../stylesheets/variables";
@import "../stylesheets/song";

.navs{
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-around;
  align-items: center;
  margin: 1% 0;
  >p{ 
    margin: 0;
    > a{
      font-family: Roboto;
      font-style: normal;
      font-weight: bold;
      font-size: 18px;
      line-height: 21px;
      color: $gray;          
    }
  }
}

.r-modal { // モーダル全体
  // vue-js-modalと喧嘩したので
  // styles=""で直接指定した(このクラスは不使用)
  background: $light_gray !important;
  border: 2px solid $modal_blue !important;
  border-radius: 7px !important;
}
.modal_body{
  position: relative;
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
  align-content: space-around;
  padding: 1%;
}
.modal_title{
  background-color: $modal_blue;
  border-radius: 7px 7px 0px 0px;
  color: white;
  font-family: Roboto;
  font-weight: bold;
  font-size: 24px;
  line-height: 56px;
  text-align: center;

  width: inherit;
  height: 56px;
}

.modal_subtitle { // ソートとかフィルターでh3にしてるやつ
  background-color: $modal_blue;
  padding: 3px 0 3px 1em;

  font-family: Roboto;
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
  color: white;
}

.button_area{ // 決定ボタン（右寄せ）
  display: flex;
  flex-direction: row-reverse;
  .modal_button{
    margin: 5%;
    padding: 0 10px;
    color: $gray;
    background-color: white;
    border: 2px solid $modal_blue;
    border-radius: 15px 5px;
    width: 140px;
    height: 48px;

    font-family: Roboto;
    font-weight: bold;
    font-size: 24px;
    line-height: 48px;
    text-align: center;
    &:hover{
      text-decoration: none;
      cursor: pointer;
    }
  }
}

</style>