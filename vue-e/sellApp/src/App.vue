<template>
    <div class="page">
        <v-head v-bind:seller="seller"></v-head>
        <div class="tab border-1px">
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

        <router-view></router-view>
    </div>
</template>

<script>
import head from './components/head/head.vue';

const ERR_OK = 0;/* 状态码 */

export default{
  data () {
    return {
      seller: {}
    };
  },
  created () {
    this.$http.get('/api/seller').then((response) => {
      // console.log(response.data);
      // console.log(response.data.errno);
      if (response.data.errno === ERR_OK) {
        this.seller = response.data;
        // console.log(this.seller);
      };
    });
  },
  components: {
    'v-head': head
  }
};
</script>

<style lang="less" scoped>

@import "./common/style/mixin.less";
@color: rgba(7,17,27,0.1);

.page{
  .tab{
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
    .maxin-1px(@color);
    .tab-item{
      flex:1;
      text-align: center;
      a{
        display: block;
        font-size: 28px;
        color: rgb(77,85,93);
      }
      .v-active{
        color: rgb(240,20,20);
      }
    }
  }
}
</style>
