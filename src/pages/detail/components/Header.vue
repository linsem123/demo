<template>
  <div>
    <router-link tag="div" to="/" class="header-ads" v-show="showFlag">
      <div class="iconfont ads-back-icon">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-show="!showFlag" :style="opacityStyle">
      <router-link to="/">
        <div class="iconfont fixed-back-icon">&#xe624;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>
<script>
export default {
  name: "DetailHeader",
  data (){
    return{
      showFlag:true,
      opacityStyle:{
        opacity:0
      }
    }
  },
  methods:{
    handleScroll(){
      const top = document.documentElement.scrollTop
      if(top>60){
        let opacity=top/140
        opacity=opacity>1?1:opacity
        this.opacityStyle={opacity}
        this.showFlag=false
      }else{
         this.showFlag=true
      }
    }
  },
  activated(){
    window.addEventListener('scroll',this.handleScroll)
  },
  deactivated (){
    window.removeEventListener('scroll',this.handleScroll)
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header-ads
  position: absolute
  top: 0.2rem;
  left: 0.2rem;
  width: 0.8rem;
  height: 0.8rem;
  border-radius: 0.4rem
  background: rgba(0, 0, 0, 0.7)
  text-align: center
  line-height: 0.8rem
  .ads-back-icon 
    color: #fff
    font-size: 0.4rem
.header-fixed
  position :fixed
  z-index :2
  top:0
  left :0
  right :0
  height :$headerHeight
  line-height :$headerHeight
  color :#fff
  font-size :.32rem
  background :$bgColor
  text-align :center
  .fixed-back-icon
    position :absolute
    top:0
    left :0
    height :.64rem
    font-size :.4rem
    text-align :center
    color :#fff
</style>