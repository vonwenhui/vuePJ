<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市，景点，游玩主题
    </div>
    <div class="header-right">
      {{this.city}}
      <span class="iconfont arrow-icon">&#xeb6d;</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    display: flex
    line-height: .86rem
    background-color :$bgColor
    color :#fff
    .header-left
      width: .64rem
      float: left
      .back-icon
        text-align :center
        font-size :.4rem
    .header-input
      flex: 1
      background :#fff
      border-radius : .1rem
      margin : .12rem .2rem
      padding-left:.4em
      line-height : .62rem
      color :#ccc
    .header-right
      width: 1.24rem
      float: right
      text-align :center
      .arrow-icon
        font-size: .2rem
        margin-left :-.04rem
</style>
