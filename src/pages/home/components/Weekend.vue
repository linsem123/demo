<template>
    <div>   
        <div class="title">
            周末去哪儿
        </div>
        <ul>
            <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
                <div class="item-img-wrapper">
                    <img class="item-img" :src="item.imgUrl"/>
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
    export default{
        name:'HomeWeekend',
        data () {
           return{
                recommendList:[{
                id: '001',
                imgUrl:'http://img1.qunarzz.com/sight/source/1505/7d/df6ff468331c43.jpg_r_640x214_1f3783d0.jpg',
                title:'大连海洋馆',
                desc:'我们一起学猫叫，一起喵喵喵',
            },{
                id:'002',
                imgUrl:'http://img1.qunarzz.com/sight/source/1511/1d/fe098e8cfec117.jpg_r_640x214_a9be292a.jpg',
                title:'大连海洋馆',
                desc:'我们一起学猫叫，一起喵喵喵',
            },{
                id:'003',
                imgUrl:'http://img1.qunarzz.com/sight/source/1511/1d/fe098e8cfec117.jpg_r_640x214_a9be292a.jpg',
                title:'大连海洋馆',
                desc:'我们一起学猫叫，一起喵喵喵',
            }]
           }
        }
    }
</script>
<style lang="stylus" scoped>
@import '~styles/mixins.styl'
    .title
        margin-top:.2rem
        background:#eee
        height:.8rem
        line-height:.8rem
    .item-img-wrapper
        overflow :hidden;
        height :0;
        padding-bottom :33.9%;
        .item-img
            width:100%
    .item-info
        padding:.1rem
        .item-title
            line-height:.54rem
            font-size:.32rem
            ellipsis()
        .item-desc
            line-height:.54rem
            color:#ccc
            ellipsis()
</style>