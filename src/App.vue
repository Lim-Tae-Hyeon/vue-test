<template>
  <div class="wrap">
    <HeaderPage :class="isMenuOpened" msg="Welcome to Your Vue.js App" @toggleMenu="isMenuOpened = isMenuOpened == 'menuOff' ? '' : ''"/>
    <div class="container">
      <LnbPage @toggleMenu="isMenuOpened = isMenuOpened == 'menuOff' ? '' : ''"/>
      <ContentPage />
    </div>
  </div>
</template>

<script>
import '@/assets/reset.css'
// import HelloWorld from './components/HelloWorld.vue'
import HeaderPage from './components/HeaderPage.vue';
import LnbPage from './components/LnbPage.vue';
import ContentPage from './components/ContentPage.vue';

export default {
  name: 'App',
  props: {
    msg: String
  },
  data () {
    return {
      isMenuOpened : '',
    }
  },
  components: {
    HeaderPage,
    LnbPage,
    ContentPage,
  }
}
</script>

<style scoped>
.container{display:flex;}
.content {padding:10px;flex-grow:1;}
</style>
