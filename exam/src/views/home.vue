<template>
  <div>
    <div class="m-swiper">
      <swiper :options="swiperOption" ref="mySwiper">
        <!-- slides -->
        <swiper-slide>I'm Slide 1</swiper-slide>
        <swiper-slide>I'm Slide 2</swiper-slide>
        <swiper-slide>I'm Slide 3</swiper-slide>
        <swiper-slide>I'm Slide 4</swiper-slide>
        <swiper-slide>I'm Slide 5</swiper-slide>
        <swiper-slide>I'm Slide 6</swiper-slide>
        <swiper-slide>I'm Slide 7</swiper-slide>
        <!-- Optional controls -->
      </swiper>
    </div>
    <div>{{tabList[curIndex*1-1].content}}</div>
    <div class="footer">
      <li
        v-for="item in tabList"
        :key="item.id"
        :class="{active:curIndex==item.id}"
        @click="changeIndex(item.id)"
      >{{item.name}}</li>
    </div>
  </div>
</template>

<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  components: {
    swiper,
    swiperSlide
  },
  data() {
    return {
      swiperOption: {
        // some swiper options/callbacks
        // 所有的参数同 swiper 官方 api 参数
        // ...
        autuplay: true,
        loop: true
      },
      tabList: [
        {
          name: "首页",
          id: 1,
          content: "123"
        },
        {
          name: "我的",
          id: 2,
          content: "456"
        }
      ],
      curIndex: 1
    };
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.swiper;
    }
  },
  mounted() {
    // current swiper instance
    // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
    console.log("this is current swiper instance object", this.swiper);
    // this.swiper.slideTo(3, 1000, false);
  },
  methods: {
    changeIndex(id) {
      this.curIndex = id;
      console.log(id, this.curIndex);
    }
  }
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  list-style: none;
}
.footer {
  display: flex;
  position: absolute;
  bottom: 0;
}
.active {
  color: red;
}
</style>