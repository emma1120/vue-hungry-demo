<template>
  <div id="app">
     <v-header :seller="seller"> </v-header>
     <div class="tab">
        <div class="tab-item">
           <router-link to="/goods">商品</router-link>  
        </div>
        <div class="tab-item">
          <router-link to="/ratings">评论</router-link> 
        </div>
        <div class="tab-item">
           <router-link to="/seller">商家</router-link> 
        </div>
     </div>
    <keep-alive>
      <router-view></router-view>   
    </keep-alive>

  </div>
</template>

<script>
import header from './components/header/header.vue'
import axios from 'axios'
export default {
  data () {
    return {
      seller: {}
    }
  },
  created () {
    axios.get('static/data.json').then((res) => {
      this.seller = res.data.seller
      console.log(this.seller)
    })
  },
  components: {
    'v-header': header
  }
}
</script>
<style lang="stylus" rel="stylesheet/stylus">
  @import 'common/stylus/index'
  .tab
   display:flex
   width:100%
   height:40px
   line-height:40px
   border-1px(rgba(7,17,27,0.1))
   .tab-item
    flex:1
    text-align:center
    a
     display:block
     font-size:14px
     color: rgb(77,85,93)
     text-decoration:none
     &.active
      font-size:14px
      color: rgb(240,20,20)
</style>
