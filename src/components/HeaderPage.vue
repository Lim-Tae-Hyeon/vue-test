<template>
  <div class="header">
    <h1>logo</h1>
    <ul class="gnb">
      <li>
        <a href="#none">메뉴1</a>
        <ul>
          <li><a href="#none">메뉴1-1</a></li>
          <li><a href="#none">메뉴1-2</a></li>
          <li><a href="#none">메뉴1-3</a></li>
        </ul>
      </li>
      <li>
        <a href="#none">메뉴2</a>
        <ul>
          <li><a href="#none">메뉴2-1</a></li>
          <li><a href="#none">메뉴2-2</a></li>
          <li><a href="#none">메뉴2-3</a></li>
        </ul>
      </li>
      <li></li>
    </ul>
  </div>
</template>

<script>
// import { ref } from 'vue';

export default {
  props:{
    msg:String
  }
}
</script>

<style scoped>
.header{display:flex;align-items:center;background-color:antiquewhite;}
.gnb{position:relative;display:flex;margin-left:40px;z-index:1;}
.gnb>li{position:relative;margin:0 10px;}
.gnb>li>a{display:block;padding:10px;margin-left:10px;}
.gnb li>ul{position:absolute;left:0;width:max-content;max-height:0;overflow:hidden;background-color:cornsilk;transition:all .3s;box-sizing:border-box;}
.gnb li>ul>li{margin:5px;}
.gnb li>ul a{display:block;padding:5px 10px;}
.gnb li:hover>ul{max-height:100px;}
</style>
