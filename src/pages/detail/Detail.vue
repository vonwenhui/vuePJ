<template>
  <div>
    <detail-banner></detail-banner>
    <detail-header></detail-header>
    <div class="fakeContent"></div>
  </div>
</template>

<script>
import DetailBanner from './componets/Banner'
import DetailHeader from './componets/Header'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader
  }
}
</script>

<style lang="stylus" scoped>
  .fakeContent
    height :50rem
</style>
