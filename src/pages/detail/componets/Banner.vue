<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-num"><span class="iconfont banner-icon">&#xe647;</span>{{this.galleryImgs.length}}</div>
      </div>
    </div>
    <common-gallery v-show="showGallery"
                    :imgs="galleryImgs"
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
  props: {
    sightName: String,
    bannerImg: String,
    galleryImgs: Array
  },
  data () {
    return {
      showGallery: false
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
