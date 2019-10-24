<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <div class="recommend-content">
      <div class="recommend-item" v-for="item of recommendLists" :key="item.id">
          <img :src="item.imgUrl">
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
        {id: '001', title: '东京-山梨 1天跟团游', desc: '日本东京一日游  富士山+忍野八海+御殿场奥特莱斯/温泉泡汤(可选酒店接送)', price: '99', imgUrl: '//imgs.qunarzz.com/vs_ceph_vs_tts/d22d164d-8c7a-454e-90e2-5d277b7249eb.jpg_180x120_d4bb5dff.jpg'},
        {id: '002', title: '大连圣亚海洋世界', desc: '浪漫大连首站，浪漫的海洋主题乐园', price: '99', imgUrl: '//imgs.qunarzz.com/p/tts8/1709/dc/b61e4a075f767a02.jpg_180x120_7b148634.jpg'},
        {id: '003', title: '大连圣亚海洋世界', desc: '浪漫大连首站，浪漫的海洋主题乐园', price: '99', imgUrl: '//imgs.qunarzz.com/vs_ceph_vs_tts/af255e15-dfc8-445d-872c-fc26da160189.jpg_180x120_171887b5.jpg'},
        {id: '004', title: '大连圣亚海洋世界', desc: '浪漫大连首站，浪漫的海洋主题乐园', price: '99', imgUrl: '//imgs.qunarzz.com/p/tts4/1709/22/751239143eeab902.jpg_180x120_51e9acdf.jpg'}
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
      width :50%
      margin :.4em auto
      img
        border-radius :.2rem
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
