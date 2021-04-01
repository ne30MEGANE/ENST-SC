<template>
  <div id="app">
    <Header />
    <ul class="nav uk-flex-around" uk-tab>
      <li><a>Songs</a></li>
      <li><a>Others</a></li>
    </ul>
    <div class="uk-switcher uk-margin">
      <section>
        <Songs />
      </section>
      <section><Others /></section>
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header'
import Songs from './components/Songs'
import Others from './components/Others'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Songs,
    Others,
    Footer
  }
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans&family=Roboto:wght@700&display=swap");

@import "stylesheets/variables";

#app {
  width: 100%;
  .uk-tab{
    a{
      padding-bottom: 0;
      font-family: 'Roboto', sans-serif;
      font-weight: bold;
      font-size: 38pt;
      text-transform: none;
      border-bottom-width: 4px;
    }
    .uk-active{
      a{
        border-color: $shadow_blue;
      }
    }
    &::before{
      border: none;
    }
  }
}
</style>
