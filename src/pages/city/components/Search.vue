<template>
    <div class="search">
        <input type="text" placeholder="请输入城市名称" class="search-input"/>
    </div>
</template>
<script>
export default {
    name:'CitySearch'
}
</script>
<style lang="stylus" scoped>
@import "~styles/varibles.styl"
.search
    background :$bgColor
    height :.72rem
    padding :0 0.1rem
    .search-input
        box-sizing:border-box
        height :.62rem
        padding :0 0.1rem
        width :100%
        color :#666
        text-align :center
        border-radius: 0.06rem
</style>


