<template>
  <div>
    <detail-banner :sightName="sightName" :bannerImg="bannerImg" :gallaryImgs="gallaryImgs"></detail-banner>
    <detail-header></detail-header>
    <div class="container">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>
<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name:'Detail',
  data(){
    return{
      list:[],
      sightName:'',
      bannerImg:'',
      gallaryImgs:[]
    }
  },
  components:{
    DetailBanner,
    DetailHeader,
    DetailList
  },
  methods:{
    getDetail(){
      axios.get('/api/detail.json',{
        params:{
          id:this.$route.params.id
        }
      }).then(this.getDetailSucc)
    },
    getDetailSucc(res){
      res=res.data
      if(res.ret&&res.data){
        const data =res.data
        this.list=data.categoryList
        this.sightName=data.sightName
        this.bannerImg=data.bannerImg
        this.gallaryImgs=data.gallaryImgs
      }
    }
  },
  mounted(){
    this.getDetail()
  }
}
</script>
<style lang="stylus" scoped>
.container{
  height :50rem
}
</style>