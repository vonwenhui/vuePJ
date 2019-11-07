<template>
  <div class="icons">
      <swiper>
        <swiper-slide v-for="(page, index) of pages" :key="index">
          <div v-for="item of page" :key="item.id" class="icon">
              <div class="icon-img">
                  <img :src=item.iconUrl>
              </div>
              <p class="icon-name">{{item.name}}</p>
          </div>
        </swiper-slide>
      </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    lists: Array
  },
  computed: {
    pages () {
      const pages = []
      this.lists.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .icons >>> .swiper-container
    height :0
    padding-bottom :50%
    margin :.1rem 0
  .icons
    margin-top :.2rem
    .icon
      position :relative
      width :25%
      height :0
      float :left
      padding-bottom :25%
      text-align :center
      .icon-img
        overflow :hidden
        position :absolute
        top :0
        left :0
        right : 0
        bottom : .44rem
        img
          height :100%
      .icon-name
        position :absolute
        bottom :0
        left :0
        right :0
        line-height :.44rem
        color :$darkTextColor
        text-align :center
        ellipsis()
</style>
