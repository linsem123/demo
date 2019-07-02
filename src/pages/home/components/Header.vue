<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe63f;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe613;</span>
            输入城市景点
        </div>
        <router-link to="/city">
            <div class="header-right">           
                {{this.city}}
                <span class="iconfont arrow-icon">&#xe654;</span>
            </div>
        </router-link>
    </div>
</template>
<script>
import {mapState} from 'vuex'
    export default{
        name:'HomeHeader',
        computed:{
            //state里的数据映射到计算属性，可以是数组也可以是对象
            ...mapState(['city'])
        }
    }
</script>
<style lang="stylus" scoped>
// 1rem=html font-size=50px
@import '~styles/varibles.styl'
.header
    line-height :$headerHeight
    display:flex
    background: $bgColor
    color:#fff
    .header-left
        width: .64rem
        float:left
        .back-icon
            font-size:.4rem
            text-align:center
    .header-input
        flex:1
        height: .64rem
        line-height:.64rem
        margin-top:.12rem
        margin-left:.2rem
        padding-left:.2rem
        background:#fff
        color:#ccc
        border-radius .1rem
    .header-right
        min-width: 1.04rem
        padding :0 0.1rem
        float:right
        text-align:center
        color :#fff
        .arrow-icon
            margin-left :-0.04rem
            font-size:.24rem

</style>
