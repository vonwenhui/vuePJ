<template>
  <div>
    <home-header :city="city"></home-header>
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
      city: '',
      swiperLists: [],
      iconLists: [],
      recommendLists: [],
      weekendLists: []
    }
  },
  mounted () {
    this.getHomeInfo()
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json').then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        this.city = res.data.city
        this.swiperLists = res.data.swiperLists
        this.iconLists = res.data.iconLists
        this.recommendLists = res.data.recommendLists
        this.weekendLists = res.data.weekendLists
      }
    }
  }
}
</script>

<style scoped>

</style>
