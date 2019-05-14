<template>
  <div>
    <div class="item border-bottom" v-for="(item,index) of list" :key="index">
      <div class="item-title">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <detail-list v-if="item.children" :list="item.children" class="item-children"></detail-list>
    </div>
  </div>
</template>
<script>
export default {
  name:'DetailList',
  props:{
    list:Array
  }
}
</script>
<style lang="stylus" scoped>
.item-title
  line-height :.8rem
  font-size:.32rem
  padding:0 .2rem
.item-title-icon
  position :relative
  left :.06rem
  top :.06rem
  display: inline-block
  background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
  margin-right: .1rem
  margin-top: .1rem
  background-size: .4rem 3rem
  width :.36rem
  height :.36rem
.item-children
  padding:0 .2rem
</style>
