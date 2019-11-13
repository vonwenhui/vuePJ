<template>
  <div id="app">
   <!-- keep-alive全部页面缓存，exclude除了哪个页面 -->
    <keep-alive exclude="Detail">
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
