<template>
  <div>
      <router-link to="/" class="header-abs" v-show="!showFixedHeader">&lt;</router-link>
      <div class="header-fixed" v-show="showFixedHeader" :style="opacityStyle">
        景点详情
        <router-link to='/'>
          <div class="iconfont header-fixed-back">&#xe624;</div>
        </router-link>
      </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showFixedHeader: false,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.showFixedHeader = true
      } else {
        this.showFixedHeader = false
      }
    }
  },
  // 使用keep-alive后会增加actived和deactived两个生命周期钩子
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  // 页面隐藏时要解绑window事件
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header-abs
    position :absolute
    left: .2rem
    top :.2rem
    width :.6rem
    height :.6rem
    border-radius : .3rem
    background :rgba(0,0,0,.8)
    color :#fff
    line-height :.6rem
    text-align :center
  .header-fixed
    z-index :2
    position :fixed
    top :0
    left :0
    right :0
    height :$headerHeight
    line-height :$headerHeight
    color :#fff
    background :$bgColor
    font-size :.32rem
    text-align :center
    .header-fixed-back
      width: .64rem
      text-align :center
      font-size :.4rem
      position :absolute
      left :0
      top :0
      color :#fff
</style>
