<template>
  <div>
    <div class="search">
      <input v-model="keyword" type="text" placeholder="请输入城市名称或拼音" class="search-input">
    </div>
    <div class="search-list" ref="search" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" v-for="item of list" :key="item.id"  @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配的数据</li>
      </ul>
    </div>
  </div>
</template>
<script>
import BScroll from "better-scroll";
import {mapMutations} from 'vuex'
export default {
  name: "CitySearch",
  data() {
    return {
      keyword: "",
      list: [],
      timer: null
    };
  },
  props: {
    cities: Object
  },
  methods:{
     handleCityClick (City){
      this.changeCity(City)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  watch: {
    keyword() {
      if (this.timer) {
        clearTimeout(this.timer);
      }
      if(!this.keyword){
          this.list=[]
          return
      }
      this.timer = setTimeout(() => {
        const result = [];
        for (let i in this.cities) {
          this.cities[i].forEach(value => {
            if (
              value.spell.indexOf(this.keyword) > -1 ||
              value.name.indexOf(this.keyword) > -1
            ) {
              result.push(value);
            }
          });
        }
        this.list = result;
      }, 100);
    }
  },
  mounted (){
      this.scroll=new BScroll(this.$refs.search)
  },
  computed:{
      hasNoData(){
          return !this.list.length
      }
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.search {
  background: $bgColor;
  height: 0.72rem;
  padding: 0 0.1rem;

  .search-input {
    box-sizing: border-box;
    height: 0.62rem;
    padding: 0 0.1rem;
    width: 100%;
    color: #666;
    text-align: center;
    border-radius: 0.06rem;
  }
}

.search-list {
  overflow: hidden;
  z-index: 1;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
  background: #eee;

  .search-item {
    background: #fff;
    color: #666;
    padding-left: 0.2rem;
    line-height: 0.62rem;
  }
}
</style>


