<template>
<div class="lnb_wrap" :class="lnbOff == true ? 'on' : 'off'">
  <div class="lnb_container">
    <div class="lnb">
      <ul class="lnb_depth2">
        <li v-for="(depth2, depth2Idx) in depth2s" :key="depth2Idx" :class="{'active': depth2Idx == depth2Index}">
          <a href="#none" @click="depth2Index = depth2Idx">{{ depth2.title }}</a>
          <ul class="lnb_depth3" v-if="depth2.depth3s.length > 0">
            <li v-for="(depth3, depth3Idx) in depth2.depth3s" :key="depth3Idx" :class="{'active': depth3Idx == depth3Index}">
              <a href="#none" @click="depth3Index = depth3Idx">{{ depth3.title }}</a>
              <ul class="lnb_depth4" v-if="depth3.depth4s.length > 0">
                <li v-for="(depth4, depth4Index) in depth3.depth4s" :key="depth4Index">
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
  <button @click="lnbOff ? lnbOff = false : lnbOff = true;" class="btn_close">닫기버튼</button>
</div>
</template>

<script>
export default {
  data() {
    return {
      lnbOff: true,
      depth2BeforeIdx : null,//마지막에 누른 메뉴 인덱스를 저장 231006 추가
      depth2Index : 0,
      depth3BeforeIdx : null,
      depth3Index : -1,
      depth3Open : false,
      depth2s: [
        {
          title : 'depth2-1',
          depth3s : [
            {
              title : 'depth3-1',
              depth4s : ['depth4-1','depth4-2']
            },
            {
              title : 'depth3-2',
              depth4s : ['depth4-1','depth4-2']
            }
          ]
        },
        {
          title : 'depth2-2',
          depth3s : [
            {
              title : 'depth3-3',
              depth4s : ['depth4-1','depth4-2']
            },
            {
              title : 'depth3-4',
              depth4s : []
            }
          ]
        },
        {
          title : 'depth2-3',
          depth3s : [
            {
              title : 'depth3-5',
              depth4s : []
            }
          ]
        },
      ]
    }
  },
	methods: {
    // depth2Click(targetIndex){
    //   console.log(targetIndex);
    //   if(targetIndex == this.depth2BeforeIdx){//현재 누른 인덱스와 이전에 누른 인덱스를 비교해서 같으면, 열린 메뉴를 또 클릭해서 메뉴를 닫으려고 한다고 판단... 메뉴 인덱스를 초기화하고 리턴
    //     this.depth2Index = -1;
    //     this.depth2BeforeIdx = null;
    //     return;
    //   }
    //   this.depth2Index = targetIndex;
    //   this.depth2BeforeIdx = targetIndex;//231006 추가 : 현재 누른 메뉴의 인덱스와 비교를 위해, 이전에 누른 메뉴 인덱스를 저장해둠
    // },
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content{background-color: red;}
.lnb_wrap{position:relative;width:100px;padding:10px;margin-right:20px;background-color: aquamarine;transition: margin-left .3s;}
.lnb_wrap.off{margin-left: -120px;}
.lnb a{display:block;margin: 10px 0;}
.lnb_depth2>li.active .lnb_depth3{display: block}
.lnb_depth3{display:none;margin-left: 10px;border: 1px solid #000;}
.lnb_depth3>li.active .lnb_depth4{display: block}
.lnb_depth4{display:none;margin-left: 20px;border: 1px solid red;}
.lnb_wrap.off .btn_close {position: absolute;right:-20px;top:0;}

</style>
