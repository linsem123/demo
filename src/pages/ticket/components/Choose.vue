<template>
    <div>
        <div class="choose border-bottom">
            <div class="kind" @click="handleKindShow" ref="changeColor">
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
        <div v-show="!allshow">
            <ticket-kinds :kindlist="kindlist" class="list"></ticket-kinds>     
            <div class="back-shadow"></div>
        </div>
    </div>
</template>

<script>
import TicketKinds from './Kinds'

export default {
    name:'TicketChoose',
    components:{
        TicketKinds
    },
    props:{
        kindlist:Array
    },
    data:function(){
        return{
            allshow:true,
            recommendshow:true
        }
    },
    methods:{
        handleKindShow(){
            this.allshow=!this.allshow
            if(this.allshow){
                this.$refs.changeColor.style.color = '#212121'            
            }else{
                this.$refs.changeColor.style.color = '#00afc7'
            }        
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
        color: #212121
        .iconfont
            color : #212121
.list
    position :absolute
    height :4.8rem
    width :100%
    z-index :10
    background :#f1f1f1
.back-shadow
    position :absolute
    z-index :9
    top :1.72rem
    left :0
    right :0
    bottom :0
    background :rgba(0,0,0,0.45)
</style>
