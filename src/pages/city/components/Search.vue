<template>
  <div>
    <div class="search">
      <input v-model="keyword" type="text" placeholder="输入城市名或拼音">
    </div>
    <div v-show="keyword" class="search-content" ref="search">
      <ul>
        <li class="search-item border-bottom" v-show="!list.length">没找到该城市</li>
        <li class="search-item border-bottom"
            v-for="item in list"
            :key="item.id"
            @click="handleCityClick(item.name)"
            >{{item.name}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapMutations} from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach(element => {
            if (element.spell.indexOf(this.keyword) > -1 ||
            element.name.indexOf(this.keyword) > -1) {
              result.push(element)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
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
  .search
    background :$bgColor
    height :.72rem
    padding : 0 .1rem
    text-align :center
    input
     box-sizing :border-box
     width :100%
     height :80%
     border-radius :.06rem
     text-align :center
     color :#666
     padding :0 .1rem
  .search-content
    z-index :1
    overflow :hidden
    position :absolute
    top : 1.58rem
    left :0
    right :0
    bottom :0
    background :#eee
    .search-item
      line-height :.62rem
      padding-left :.2rem
      color :#666
      background :#fff
 </style>
