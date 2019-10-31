<template>
  <div class="search">
    <input type="text" placeholder="输入城市名或拼音">
  </div>
</template>

<script>

export default {
  name: 'CitySearch'
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
 </style>
