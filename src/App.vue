<template>
  <div id="app">
    <div id="grad_u"></div>
    <div id="grad_r"></div>
    <div id="grad_d"></div>
    <div id="grad_l"></div>
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
  height: 100%;
  #grad_u,#grad_r,#grad_d,#grad_l {
    position: fixed;
    z-index: 10;
    margin: -15px;
    padding: 0;
  }
  #grad_u,#grad_d {
    left: 0;
    width: 100%;
    height: 0;
  }
  #grad_r,#grad_l {
    top: 0;
    width: 0;
    height: 100%;
  }
  #grad_u {
    top: 0;
    box-shadow: 0 15px 15px 15px $shadow_blue;
  }
  #grad_r {
    right: 0;
    box-shadow: -15px 0 15px 15px $shadow_blue;
  }
  #grad_d {
    bottom: 0;
    box-shadow: 0 -15px 15px 15px $shadow_blue;
  }
  #grad_l {
    left: 0;
    box-shadow: 15px 0 15px 15px $shadow_blue;
  }
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
