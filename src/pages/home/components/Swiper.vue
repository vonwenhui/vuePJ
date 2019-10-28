<template>
  <div class="wrapper">
    <swiper>
      <!-- slides -->
      <swiper-slide v-for="item of Lists" :key="item.id"><img class="swiper-img" :src=item.imgUrl></swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    Lists: Array
  },
  data: function () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        },
        loop: true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background-color :#fff
  .wrapper
    overflow :hidden
    width :100%
    height :0
    padding-bottom :31.25%
    .swiper-img
      width :100%
</style>
