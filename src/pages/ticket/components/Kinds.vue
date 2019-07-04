<template>
    <div class="box">
        <div class="list-left" ref="wripper">
            <ul class="kinds">
                <li 
                v-for="item of kindlist" 
                :key="item.id" 
                @click="handleClickKinds(item.id)"
                class="kinds-list border-bottom">
                    <img class="kind-img" :src="item.image"/>
                    <span>{{item.name}}</span>
                    <span class="kind-number">{{item.count}}</span>
                </li>
            </ul>
        </div>
        <div class="list-right">
            <ul>
                <li></li>
            </ul>
        </div>
    </div>
</template>

<script>
import BScroll from "better-scroll";

export default {
    name:'TicketKinds',
    data:function(){
        return {
            children:[]
        }
    },
    props:{
        kindlist:Array
    },
    methods:{
        handleClickKinds(id){
        let __this  = this;
            this.kindlist.forEach(function(v,i){
               
               if(v.id === id){
               
                   
                   console.log(v.children)
                   __this.children = v.children
               }
            })
        }
    },
    mounted(){
        const options = {
            scrollY: true,
            click: true
        }
        // fade 默认为 true，滚动条淡入淡出
        options.scrollbar = true
        // 滚动条一直显示
        options.scrollbar = {
        fade: false
        }
        this.scroll = new BScroll(this.$refs.wripper,options);
    }
}
</script>

<style lang="stylus" scoped>
.list-left>>> .bscroll-vertical-scrollbar
     right :50% !important 
.box
    display :flex
    .list-left
        flex :1
        background :white
        height :100%
        overflow hidden 
        .kinds-list:first-of-type
            background :#f1f1f1       
        .kinds-list
            line-height :.8rem 
            height :.8rem            
            .kind-img 
                width :.3rem
                height :.3rem
                margin :0 .06rem .06rem .2rem
            .kind-number
                float :right;
                margin-right :.2rem 
        
    .list-right
        flex :1
        visibility :hidden
</style>
