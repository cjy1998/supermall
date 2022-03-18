<template>
  <div id="category">
    <nav-bar class="category-nav">
      <div slot="center" ><strong>分类</strong></div>
    </nav-bar>
    <div class="wrapper">
     <ul class="content">
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
       <li>dsdsaa</li>
     </ul>
    </div>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar";
import BScroll from 'better-scroll';
  export default {
    name: "Category",
    components:{
      NavBar
    },
    mounted(){
      new BScroll('.wrapper',{
        probeType: 3
      })
    
    }
  }
</script>

<style scoped>
.category-nav{
  background-color: var(--color-tint);
  color: white;
}
.wrapper{
  height: 50px;
  background-color: aqua;
  overflow: hidden;
}
</style>
