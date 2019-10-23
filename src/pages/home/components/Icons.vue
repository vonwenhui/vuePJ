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
  data: function () {
    return {
      iconLists: [
        {id: '001', name: '酒店', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/hotel.png'},
        {id: '002', name: '机票', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/flight.png'},
        {id: '003', name: '度假', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/package.png'},
        {id: '004', name: '火车票', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/train.png'},
        {id: '005', name: '景点门票', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/piao.png'},
        {id: '006', name: '酒店', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/hotel.png'},
        {id: '007', name: '酒店', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/hotel.png'},
        {id: '008', name: '酒店', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/hotel.png'},
        {id: '009', name: '第二屏', iconUrl: '//s.qunarzz.com/homenode/images/touchheader/hotel.png'}
      ]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconLists.forEach((item, index) => {
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
        // ellipsis()
</style>
