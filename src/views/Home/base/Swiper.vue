<template>
  <div class="swiper-wrapper">
    <van-swipe :autoplay="3000" indicator-color="#f60">
      <van-swipe-item v-for="(image, index) in images" :key="index" @click="goUrl">
        <img v-lazy="image.ImgUrl" />
      </van-swipe-item>
    </van-swipe>
  </div>
</template>
<script>
export default {
  data() {
    return {
      images: [], //banner 轮播图
    };
  },
  created() {
    this.$api.homeData.banner().then(({ data: { banner } }) => {
      this.images = banner;
    });
  },
  methods:{
    // 路由跳转
    goUrl(){
      this.$toast.loading({
        message: "加载中...",
        forbidClick: true,
        loadingType: "spinner"
      });
      setTimeout(()=>{
        this.$toast.clear()
        this.$router.push("/detail?goods_id=9027200515")
      },500)
    }
  }
};
</script>
<style lang="scss" scoped>
.swiper-wrapper {
  img {
    width: 100%;
  }
}
</style>
