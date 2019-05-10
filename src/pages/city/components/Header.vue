<template>
    <div class="header">
        城市选择
        <router-link to="/">
            <div class="iconfont header-icon">&#xe624;</div>
        </router-link>
    </div>
</template>
<script>
export default {
    name:'CityHeader'
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';
.header  
    position :relative
    overflow :hidden
    height :$headerHeight
    line-height :$headerHeight
    color :#fff
    font-size :.32rem
    background :$bgColor
    text-align :center
    .header-icon
        position :absolute
        top:0
        left :0
        height :.64rem
        font-size :.4rem
        text-align :center
        color :#fff
</style>


