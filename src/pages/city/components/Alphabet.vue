<template>
  <ul class="list">
    <li
      class="item"
      v-for="item of letters"
      :key="item"
      :ref="item"
      @click="listHandleClick"
      @touchstart="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd"
    >{{item}}</li>
  </ul>
</template>
<script>
export default {
  name: "CityAlphabet",
  data() {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    };
  },
  props: {
    cities: Object
  },
  updated() {
    //先在data有定义，数据改变的时候执行
    this.startY = this.$refs["A"][0].offsetTop;
  },
  computed: {
    letters() {
      //将字母存储成一个列表，根据下标找出对应的字母
      const letters = [];
      for (let i in this.cities) {
        letters.push(i);
      }
      return letters;
    }
  },
  methods: {
    listHandleClick(e) {
      this.$emit("change", e.target.innerText);
    },
    handleTouchStart() {
      this.touchStatus = true;
    },
    handleTouchMove(e) {
      //如果16ms内再次触发touchmove的操作，上一次的就清除，以达到减少这个函数执行的效果
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer);
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79;
          const index = Math.floor((touchY - this.startY) / 17);
          if (index >= 0 && index <= this.letters.length) {
            this.$emit("change", this.letters[index]);
          }
        },16);
      }
    },
    handleTouchEnd() {
      this.touchStatus = false;
    }
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.list {
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: center;
  right: 0;
  top: 1.58rem;
  bottom: 0;
  width: 0.4rem;
  color: $bgColor;

  .item {
    text-align: center;
    line-height: 0.34rem;
  }
}
</style>

