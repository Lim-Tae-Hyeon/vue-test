<template>
<div class="lnb_wrap">
  <div class="lnb_container">
    <div class="lnb">
      <ul class="lnb_depth2">
        <li v-for="(depth2, depth2Index) in depth2s" :key="depth2Index">
          <a href="#none">{{ depth2.title }}</a>
          <ul class="lnb_depth3">
            <li v-for="(depth3, depth3Index) in depth2.depth3" :key="depth3Index">
              <a href="#none">{{ depth2.depth3.title }}</a>
              <ul class="lnb_depth4" v-if="depth2.depth3.depth4.length">
                <li v-for="(depth4, depth4Index) in depth2.depth3.depth4" :key="depth4Index">
                  <a href="#none">{{ depth4 }}</a>
                </li>
              </ul>
            </li>
          </ul>
        </li>
      </ul>
    </div>
    <div class="search">
      검색영역
    </div>
  </div>
  <button @click="closeLnb()" class="btn_close">닫기버튼</button>
</div>
</template>

<script>
export default {
  data() {
    return {
      depth2s: [
        {
          title : 'depth2-1',
          depth3 : {
            title : 'depth3-1',
            depth4 : ['depth4-1','depth4-2']
          }
        },
        {
          title : 'depth2-2',
          depth3 : {
            title : 'depth3-2',
            depth4 : []
          }
        },
        {
          title : 'depth2-3',
          depth3 : {
            title : 'depth3-3',
            depth4 : ['depth4-1','depth4-2']
          }
        },
      ]
    }
  },
	methods: {
		closeLnb: function(){
      const lnbWrap = document.querySelector('.lnb_wrap');
      lnbWrap.classList.toggle('off');
    },
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content{background-color: red;}
.lnb_wrap{position:relative;width:100px;padding:10px;margin-right:20px;background-color: aquamarine;transition: margin-left .3s;}
.lnb_wrap.off{margin-left: -120px;}
.lnb a{display:block;margin: 10px 0;}
.lnb_depth3{margin-left: 10px;border: 1px solid #000;}
.lnb_depth4{margin-left: 20px;border: 1px solid red;}
.lnb_wrap.off .btn_close {position: absolute;right:-20px;top:0;}
</style>
