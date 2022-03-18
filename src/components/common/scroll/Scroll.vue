<template>
<div class="wrapper" ref="wrapper">
    <div class="content">
        <slot></slot>
    </div>
   </div>
  
</template>

<script>
import BScroll from "better-scroll"
export default {
 name: 'scroll',
 props:{
     probeType: {
         type: Number,
         default: 0
     }
 },
    data(){
       return {
           scroll: null
       } 
    },
    mounted(){
        //1.创建BScroll对象
        this.scroll = new BScroll(this.$refs.wrapper,{
            click: true,
            probeType: this.probeType
        })

        //2.监听滚动位置
        this.scroll.on('scroll',(position) => {
            //子组件自定义事件，把值传出去
            this.$emit('scroll',position)
        })
    },
    methods:{
        scrollTo(x,y,time){
            this.scroll.scrollTo(x,y,time)
        }
    }
}
</script>

<style>

</style>