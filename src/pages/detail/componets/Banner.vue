<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" src="https://imgs.qunarzz.com/sight/p0/1503/38/3877fc96dff9b532.water.jpg_710x360_12338806.jpg">
      <div class="banner-info">
        <div class="banner-title">东京迪士尼乐园</div>
        <div class="banner-num"><span class="iconfont banner-icon">&#xe647;</span>1/7</div>
      </div>
    </div>
    <common-gallery v-show="showGallery"
                    :imgs="imgs"
                    @close="handleGalleryClose"></common-gallery>
  </div>
</template>

<script>
import CommonGallery from 'common/gallery/Gallery'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallery
  },
  data () {
    return {
      showGallery: false,
      imgs: ['https://imgs.qunarzz.com/sight/p0/1503/38/3877fc96dff9b532.water.jpg_710x360_12338806.jpg',
        'https://imgs.qunarzz.com/sight/p0/1503/fc/fcd2e0e62d3537b7.water.jpg_710x360_a12f9c1c.jpg']
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position :relative
    overflow :hidden
    height :0
    padding-bottom :50%
    .banner-img
      width :100%
    .banner-info
      color :#fff
      position :absolute
      bottom :0
      left :0
      right :0
      line-height :.6rem
      display :flex
      background-image : linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8))
      .banner-title
        flex :1
        font-size :.32rem
        padding-left :.2rem
      .banner-num
        margin-top :.14rem
        padding :0 .4rem
        border-radius :.2rem
        height :.32rem
        line-height :.32rem
        background :rgba(0,0,0,.8)
        font-size :.24rem
        .banner-icon
          font-size :.24rem
</style>
