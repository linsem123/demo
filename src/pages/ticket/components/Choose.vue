<template>
    <div>
        <div class="choose border-bottom">
            <div class="kind">
                全部分类
                <span class="iconfont" v-show="allshow">&#xe655;</span>
                <span class="iconfont" v-show="!allshow">&#xe797;</span>
            </div>
            <div class="column-line"></div>
            <div class="kind">
                推荐排序
                <span class="iconfont" v-show="recommendshow">&#xe655;</span>
                <span class="iconfont" v-show="!recommendshow">&#xe797;</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'TicketChoose',
    props:{
        kindlist:Array
    },
    data:function(){
        return{
            allshow:true,
            recommendshow:true
        }
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.choose
    height :$headerHeight
    line-height :$headerHeight
    display :flex
    .column-line
        width :0
        height .6rem
        margin-top:.13rem
        border-right :.02rem solid #e0e0e0;
    .kind
        flex:1
        text-align :center

</style>
