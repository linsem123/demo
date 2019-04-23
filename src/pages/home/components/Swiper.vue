<template>
    <div class="wrapper">
        <swiper :options="swiperOption">
            <swiper-slide v-for="item of swiperList" :key="item.id">
                <img class="swiper-img" :src="item.imgUrl">
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>
<script>
export default{
    name:'HomeSwiper',
    data(){
        return {
            swiperOption: {
                pagination: '.swiper-pagination',
                loop: true
            },
            swiperList:[{
                id:'001',
                imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/26c9b54e3e02d3724f614883d77a62c6.jpg_750x200_57aa8efa.jpg'
            },{
                id:'002',
                imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/ca88075c516cf51a323c509889d34b2c.jpg_750x200_599610ae.jpg'
            }]
        }
    }
}
</script>
<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active
      background: #fff
    .wrapper
      overflow: hidden
      width: 100%
      height: 0
      padding-bottom: 26.67%
      background: #eee
      .swiper-img
        width: 100%
</style>