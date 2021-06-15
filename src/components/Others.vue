<template>
  <div class="others">
    <h3>このサイトについて</h3>
    <div class="text">
      当サイトは「もっともシンプルな楽曲一覧サイト」をコンセプトとして制作した
      あんさんぶるスターズ!!Musicのファンサイトです。<br>
      楽曲情報はゲームアプリで確認後手動で追加・管理しております。<br>
    </div>
    <h3>このサイトの使い方</h3>
    <div class="text">
      <h4>掲載内容について</h4>
      あんさんぶるスターズ!!Musicの収録楽曲情報を見ることができます。<br>
      取り扱っている情報は以下の通りです。<br>
      <ul>
        <li>楽曲名</li>
        <li>歌唱ユニット名</li>
        <li>楽曲属性</li>
        <li>楽曲レベル(Expert)</li>
      </ul>
      のんきに開発しているうちに新難易度が追加されました。<br>
      Specalの楽曲レベルもどうにか一緒に掲載したいですが、追々実装します。<br>
      <h4>ソート・フィルター機能について</h4>
      楽曲一覧を並び替えたり、フィルターをかけたりすることができます。<br>
      並び替えとフィルターの両方を指定し決定ボタンを押すことで、同時に適用することもできます。<br>
      <br>
      <h4>ランダム選曲機能について</h4>
      表示されている楽曲からランダムで1曲選んで表示します。<br>
      フィルターが指定されている場合は、その条件に当てはまる楽曲のみが選出されます。<br>
      例：フィルター[楽曲属性: <span class="Sparkle">sparkle</span> ] → Dance in the Apocalypse<br>
    </div>
    <h3>その他</h3>
    <div class="text">
      等サイトは<a href="https://www.happyelements.co.jp/contents-guideline/" target="_blank" rel="noopener noreferrer">HappyElementsコンテンツ利用ガイドライン<img src="../assets/125_arr_hoso.svg"></a>を確認し、
      "②インターネット上の利用について"に記載されている規約を満たすものという解釈の上で制作・公開しています。<br>
      今後コンテンツ利用ガイドラインの更新に伴って予告なくサイトの公開を取りやめる可能性がありますので、予めご了承ください。<br>
      <br>
      掲載情報のミスやサイトのバグ等は以下のTwitterアカウントまでお寄せいただけますと幸いです。<br>
      <a href="https://twitter.com/ed_mgn"  target="_blank" rel="noopener noreferrer">開発者Twitterアカウント<img src="../assets/125_arr_hoso.svg"></a>
    </div>
    <h3>更新情報</h3>
      <Release />
    <h3>既知のバグ</h3>
      <Bugs />
  </div>
</template>

<script>
import Release from './Release.vue'
import Bugs from './Bugs.vue'
export default {
  components:{ Release, Bugs }
  
}
</script>

<style lang="scss">
@import "../stylesheets/variables";
.others{
  width: 90%;
  margin: auto;
  font-family: 'Noto Sans', sans-serif;

  h3{
    font-weight: bold;
    border-bottom: 2px solid $light_gray;
  }
  .text{
    padding-left: 2em;
    img{
      display: inline;
      height: 1em;
      vertical-align: middle;
    }
  }
}

</style>