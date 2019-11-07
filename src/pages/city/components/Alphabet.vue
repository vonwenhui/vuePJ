<template>
  <ul class="list">
    <li v-for="(item,key) of cities" :key="key" class="item">{{key}}</li>
  </ul>
</template>

<script>

export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .list
    display :flex
    flex-direction :column
    justify-content :center
    position :absolute
    right :0
    top :1.58rem
    bottom :0
    width :.4rem
    text-align :center
    .item
      color :$bgColor
      line-height : .4rem
</style>
