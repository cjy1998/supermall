<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center" ><strong>购物街</strong></div>
    </nav-bar>
    <scroll class="content" ref="scroll" :probeType="3" @scroll="ContenScroll">
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommend="recommend"></recommend-view>
    <feature/>
    <tab-control :titles="['流行','新款','精选']" 
    class="tab-control"
    @tabclick="tabclick"/>
    <goods-list :goods="showGoods"/>
    </scroll>
    <!-- .native监听组件的原生事件 -->
    <back-top @click.native="backClick" v-show="isShowBackTop"/>
    </div>
</template>

<script>

import {getHomeMultidata,getHomeGoods} from "../../network/home";
import HomeSwiper from "./ChildComps/HomeSwiper";
import RecommendView from "./ChildComps/RecommendView";
import Feature from "./ChildComps/Feature";

import NavBar from "../../components/common/navbar/NavBar";
import TabControl from "../../components/content/tabControl/TabControl";
import Scroll from "../../components/common/scroll/Scroll.vue"

import GoodsList from "../../components/content/goods/GoodsList.vue";
import BackTop from "../../components/content/backTop/BackTop.vue"
  export default {
    name: "Home",
    components:{

      HomeSwiper,
      RecommendView,
      Feature,
      NavBar,
      TabControl,
      Scroll,
      GoodsList,
      BackTop,
    },
    data(){
      return{
      banners: [],
        recommend:[],
        goods:{
          'pop': {page: 0, list: []},
          'new': {page: 0, list: []},
          'sell': {page: 0, list: []},
        },
        currentType: 'pop', //默认
        isShowBackTop: false,
      }
    },
    created() {
      //1.请求多个数据
      this.getHomeMultidata();
      //2.请求商品数据
     this.getHomeGoods('pop');
     this.getHomeGoods('new');
     this.getHomeGoods('sell');


    },
    computed: {
      showGoods(){
        return this.goods[this.currentType].list
      }
    },
    methods: {
    /**
     * 事件监听相关
     */
      tabclick(index){
        switch (index) {
          case 0:
            this.currentType = 'pop'
            break;
          case 1:
            this.currentType = 'new'
            break;
          case 2:
            this.currentType = 'sell'
        }
        },
        // 回到顶部
        backClick(){
          
         this.$refs.scroll.scrollTo(0,0,500)
        },
        //定位
        ContenScroll(position){
          this.isShowBackTop = position.y <= -1000
        },


      /**
       * 网络请求相关
       */
       getHomeMultidata(){
          getHomeMultidata().then(res => {
        //console.log(res);
             this.banners = res.data.banner.list;
              this.recommend = res.data.recommend.list;
      })
       },
        getHomeGoods(type){
          const page = this.goods[type].page + 1
          getHomeGoods(type,page).then(res =>{
            console.log(res);
            // 依次把数据push进goods数组
            this.goods[type].list.push(...res.data.list)
            this.goods[type].page += 1
      })
        }
        
        
    }
  }
</script>

<style scoped>
#home{
  padding-top: 44px;
  height: 100vh;
  position: relative;
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
  /* position: sticky; */
  top: 44px;
  z-index: 9;
}
.content{
 overflow: hidden;
 position: absolute;
 top: 44px;
 bottom: 49px;
 left: 0;
 right: 0;
}
/* .content{
  height: calc(100% - 93px);
  overflow: hidden;
  margin-top: 44px;
} */
</style>
