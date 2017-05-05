<template>
    <div class="page">
        <v-head></v-head>
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

        <router-view></router-view>
    </div>
</template>

<script>
import head from './components/head/head.vue';
export default{
  components: {
    'v-head': head
  }
};
</script>

<style lang="less" scoped>
@import "./common/style/mixin";
@color: rgba(7,17,27,.01);
.page{
  .tab{
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
    // box-shadow: inset 0px -1px 1px -1px #c8c7cc;
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
