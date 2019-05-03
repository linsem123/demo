<template>
    <div>   
        <div class="title">
            热门营销
        </div>
        <ul>
            <li class="item border-bottom">
                <img class="item-img" src="http://img1.qunarzz.com/sight/p0/1904/65/65a949083122447da3.img.jpg_200x200_c4b2f699.jpg"/>
                <div class="item-info">
                    <p class="item-title">大连海洋馆</p>
                    <p class="item-desc">我们一起学猫叫，一起喵喵喵</p>
                    <button class="item-btn">查看详情</button>
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
    export default{
        name:'HomeRecommend'
    }
</script>
<style lang="stylus" scoped>
@import '~styles/mixins.styl'
    .title
        margin-top:.2rem
        background:#eee
        height:.8rem
        line-height:.8rem
    .item
        overflow:hidden
        display:flex
        height:1.9rem
        .item-img
            width:1.7rem
            height:1.7rem
            padding:.1rem
        .item-info
            flex:1
            padding:.1rem
            min-width:0
            .item-title
                line-height:.54rem
                font-size:.32rem
                ellipsis()
            .item-desc
                line-height:.54rem
                color:#ccc
                ellipsis()
            .item-btn
                line-height:.44rem
                background:#ff9300
                margin-top:.16rem
                padding:0 .2rem
                border-radius: .06rem
                color:#fff
</style>