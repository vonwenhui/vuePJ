<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title">当前城市</div>
        <div class="button-list-wrapper">
          <div class="button-list">
              <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title">热门城市</div>
        <div class="button-list-wrapper">
          <div class="button-list">
              <div v-for="item of hotCities"
                   :key="item.id"
                   @click="handleCityClick(item.name)"
                   class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div v-for="(item,key) of cities"
           :key="key"
           :ref="key"
           class="area">
        <div class="title">{{key}}</div>
        <div v-for="innerItem of item"
             :key="innerItem.id"
             @click="handleCityClick(innerItem.name)"
             class="item-list">
            <div class="item border-bottom">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  methods: {
    ...mapMutations(['changeCity']),
    handleCityClick (cityName) {
      this.changCity(cityName)
      this.$router.push('/')
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .border-bottom
    &:before
      border-color :#ccc
  .list
    overflow :hidden
    position :absolute
    top :1.58rem
    left :0
    right :0
    bottom :0

    .title
      background :#eee
      height :.44rem
      line-height :.44rem
      padding-left :.1rem
      color :#666
      font-size :.26rem
    .button-list-wrapper
      padding :.1rem .6rem .1rem .1rem
      .button-list
          display :flex
          flex-wrap : wrap
          .button
              text-align :center
              border :.02rem solid #ccc
              padding :.1rem 0
              margin :.1rem
              border-radius :.06rem
              width :29%
    .item-list
      padding : .2rem
      .item
        line-height :.74rem
</style>
