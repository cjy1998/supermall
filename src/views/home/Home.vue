<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center" ><strong>购物街</strong></div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommend="recommend"></recommend-view>
    <feature/>
    <tab-control :titles="['流行','新款','精选']" class="tab-control"/>
    <ul>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>
      <li>dd</li>

      <li>dd</li>
    </ul>
  </div>
</template>

<script>

import {getHomeMultidata,getHomeGoods} from "../../network/home";
import HomeSwiper from "./ChildComps/HomeSwiper";
import RecommendView from "./ChildComps/RecommendView";
import Feature from "./ChildComps/Feature";

import NavBar from "../../components/common/navbar/NavBar";
import TabControl from "../../components/content/tabControl/TabControl";
  export default {
    name: "Home",
    components:{

      HomeSwiper,
      RecommendView,
      Feature,
      NavBar,
      TabControl
    },
    data(){
      return{
      banners: [],
        recommend:[],
        goods:{
          'pop': {page: 0, list: []},
          'news': {page: 0, list: []},
          'sell': {page: 0, list: []},
        }
      }
    },
    created() {
      //1.请求多个数据
      getHomeMultidata().then(res => {
        //console.log(res);
        this.banners = res.data.banner.list;
        this.recommend = res.data.recommend.list;
      })
      //2.请求商品数据
      getHomeGoods('pop',1).then(res =>{
        console.log(res)
      })
    }
  }
</script>

<style scoped>
#home{
  padding-top: 44px;
}
.home-nav{
  background-color: var(--color-tint);
  color: white;

  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
/*tab-control滑动到指定位置固定 stick->fixed*/
.tab-control{
  position: sticky;
  top: 44px;
}
</style>
