<template>
  <div>
    <home-header></home-header>
    <home-swiper :lists="swiperLists"></home-swiper>
    <home-icons :lists="iconLists"></home-icons>
    <home-recommend :lists="recommendLists"></home-recommend>
    <home-weekend :lists="weekendLists"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      lastCity: '',
      swiperLists: [],
      iconLists: [],
      recommendLists: [],
      weekendLists: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        this.swiperLists = res.data.swiperLists
        this.iconLists = res.data.iconLists
        this.recommendLists = res.data.recommendLists
        this.weekendLists = res.data.weekendLists
      }
    }
  },
  // 页面初次加载
  mounted () {
    this.getHomeInfo()
    this.lastCity = this.city
  },
  // 每次页面加载
  activated () {
    if (this.city !== this.lastCity) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style scoped>

</style>
