<template>
  <div id="category">
    <nav-bar class="category-nav">
      <div slot="center" ><strong>分类</strong></div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar";
  export default {
    name: "Category",
    components:{
      NavBar
    }
  }
</script>

<style scoped>
.category-nav{
  background-color: var(--color-tint);
  color: white;
}
</style>
