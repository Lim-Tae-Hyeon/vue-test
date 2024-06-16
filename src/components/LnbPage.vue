<template>
<div class="lnb_wrap" :class="lnbOff == true ? 'on' : 'off'">
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
  <button @click="lnbOff ? lnbOff = false : lnbOff = true;" class="btn_close">닫기버튼</button>
</div>
</template>

<script>
export default {
  data() {
    return {
      lnbOff: true,
      // menuBeforeIdx : null,//마지막에 누른 메뉴 인덱스를 저장 231006 추가
      // menuIdx : 1,
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
    // menuOn(idx){//231006 수정
    //   console.log(this.menuBeforeIdx);
    //   if(idx == this.menuBeforeIdx){//현재 누른 인덱스와 이전에 누른 인덱스를 비교해서 같으면, 열린 메뉴를 또 클릭해서 메뉴를 닫으려고 한다고 판단... 메뉴 인덱스를 초기화하고 리턴
    //     this.menuIdx = -1;
    //     this.menuBeforeIdx = null;
    //     return;
    //   }
    //   this.menuIdx = idx;
    //   this.$emit("toggleMenu");
    //   this.menuBeforeIdx = idx;//231006 추가 : 현재 누른 메뉴의 인덱스와 비교를 위해, 이전에 누른 메뉴 인덱스를 저장해둠
    // }
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
/* 

.menulist > ul > li .depth2 {
  height: 0;
  overflow: hidden;
  transition: all 0.5s;
}

.menulist > ul > li .depth2 > ul {
  padding: 12px 0 15px;
}

.menulist > ul > li .depth2 > ul > li > a {
  position: relative;
  display: block;
  padding: 6px 0 5px 51px;
  color: #666;
  font-weight: 500;
  font-size: 15px;
}

.menulist > ul > li .depth2 > ul > li > a::after {
  content: "";
  position: absolute;
  top: calc(50% - 3px);
  left: 37px;
  background: #666;
  width: 5px;
  height: 5px;
  border-radius: 50%;
}

.menulist > ul > li .depth2 > ul > li > a:hover,
.menulist > ul > li .depth2 > ul > li.on > a {
  color: #000;
}

.menulist > ul > li .depth2 > ul > li > a:hover::after,
.menulist > ul > li .depth2 > ul > li.on > a::after {
  background: #000;
}

.menulist > ul > li.on {
  margin: 29px 0 18px;
}

.menulist > ul > li:first-child.on {
  margin-top: 0;
}

.menulist > ul > li.on > a {
  background: #12b660;
  color: #fff;
}

.menulist > ul > li.on > a i {
  background-color: transparent;
}

.menulist > ul > li.on > a i {
  background-position: 0 -60px;
}

.menulist > ul > li.on > a i img {
  margin: -60px 0 0 0;
}

.menulist > ul > li.on > .fold {
  background-position: right 20px top 15px;
}

.menulist > ul > li.on .depth2 {
  height: auto;
  overflow: hidden;
} */

</style>
