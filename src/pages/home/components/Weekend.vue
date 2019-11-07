<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <div class="recommend-content">
      <div class="recommend-item" v-for="item of lists" :key="item.id">
          <div class="img-wrapper">
            <img :src="item.imgUrl">
          </div>
          <p class="title">{{item.title}}</p>
          <p class="desc">{{item.desc}}</p>
          <p class="price"><em>{{item.price}}</em>起</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    lists: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .recommend-title
    line-height :.8rem
    text-indent :.2rem
    background :#eee
    margin-top :.2rem
  .recommend-content
    text-align :center
    display :flex
    flex-wrap :wrap
    .recommend-item
      width :100%
      margin :.4em auto
      .img-wrapper
        overflow :hidden
        height :0
        padding-bottom :37.09%
        img
          max-width : 100%
      p
        margin :.1rem .2rem
        text-align :left
      .title
        font-weight :bold
        ellipsis()
      .desc
        color :#ccc
        ellipsis()
      .price
        color :orange
</style>
