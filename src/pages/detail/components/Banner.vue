<template>
  <div>
    <div class="banner" @click="hanlegallaryShowClick">
      <img
        class="banner-img"
        :src="bannerImg"
      >
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>
          {{this.gallaryImgs.length}}
        </div>
      </div>
    </div>
    <common-gallary :img="gallaryImgs" v-show="gallaryShow" @banner-close="handleGallaryClose"></common-gallary>
    
  </div>
</template>
<script>
import CommonGallary from "common/gallary/Gallary";
export default {
  name: "DetailBanner",
  components: {
    CommonGallary
  },
  data() {
    return {
      gallaryShow: false,
    };
  },
  methods: {
    hanlegallaryShowClick() {
      this.gallaryShow = true;
    },
    handleGallaryClose(e) {
      this.gallaryShow = false;
    }
  },
  props:{
    gallaryImgs: Array,
    bannerImg:String,
    sightName:String

  }
};
</script>
<style lang="stylus" scoped>
.banner {
  overflow: hidden;
  position: relative;
  height: 0;
  padding-bottom: 55%;

  .banner-img {
    width: 100%;
  }

  .banner-info {
    position: absolute;
    display: flex;
    right: 0;
    left: 0;
    bottom: 0;
    color: #fff;
    line-height: 0.6rem;
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));

    .banner-title {
      font: size 0.32rem;
      flex: 1;
      padding: 0 0.2rem;
    }

    .banner-number {
      font-size: 0.24rem;
      line-height: 0.32rem;
      height: 0.32rem;
      margin-top: 0.14rem;
      padding: 0 0.4rem;
      background: rgba(0, 0, 0, 0.6);
      border-radius: 0.2rem;

      .banner-icon {
        font-size: 0.24rem;
      }
    }
  }
}
</style>

