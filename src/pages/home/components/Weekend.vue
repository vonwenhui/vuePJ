<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <div class="recommend-content">
      <div class="recommend-item" v-for="item of recommendLists" :key="item.id">
          <div class="img-wrapper">
            <img :src="item.imgUrl">
          </div>
          <p class="title">{{item.title}}</p>
          <p class="desc">{{item.desc}}</p>
          <p class="price"><em>{{item.price}}</em>起</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data: function () {
    return {
      recommendLists: [
        {id: '001', title: '东京-山梨 1天跟团游', desc: '日本东京一日游  富士山+忍野八海+御殿场奥特莱斯/温泉泡汤(可选酒店接送)', price: '99', imgUrl: 'http://www.ghibli-museum.jp/img/mainimg.png'},
        {id: '002', title: '大连圣亚海洋世界', desc: '浪漫大连首站，浪漫的海洋主题乐园', price: '99', imgUrl: '//mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/201910/abe3418971067bd655fb2794d6e2eeec.jpg'},
        {id: '003', title: '大连圣亚海洋世界', desc: '浪漫大连首站，浪漫的海洋主题乐园', price: '99', imgUrl: '//mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20199/387c5e767cccc7a3172ed7ea15b50727.png'}
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .recommend-title
    line-height :.8rem
    text-indent :.2rem
    background :#eee
    margin-top :.2rem
  .recommend-content
    text-align :center
    display :flex
    flex-wrap :wrap
    .recommend-item
      width :100%
      margin :.4em auto
      .img-wrapper
        overflow :hidden
        height :0
        padding-bottom :33.9%
        img
          max-width : 100%
      p
        margin :.1rem .2rem
        text-align :left
      .title
        font-weight :bold
        ellipsis()
      .desc
        color :#ccc
        ellipsis()
      .price
        color :orange
</style>
