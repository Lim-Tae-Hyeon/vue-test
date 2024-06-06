<template>
  <div class="wrap">
    <VueHearder msg="Welcome to Your Vue.js App"/>
    <div class="container">
      <VueLnb />
      <div class="content">컨텐츠영역</div>
    </div>
  </div>
</template>

<script>
import '@/assets/reset.css'
// import HelloWorld from './components/HelloWorld.vue'
import VueHearder from './components/VueHearder.vue';
import VueLnb from './components/VueLnb.vue';

export default {
  name: 'App',
  components: {
    VueHearder,
    VueLnb
  }
}
</script>

<style scoped>
.container{display:flex;}
.content {padding:10px;flex-grow:1;}
</style>
