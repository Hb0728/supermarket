<template>
  <div class="wrapper" ref="wrapper">
      <div class="content">
          <slot></slot>
      </div>
  </div>
</template>

<script>
import bscroll from 'better-scroll'
import PullUp from '@better-scroll/pull-up'
bscroll.use(PullUp)
export default {
    name:'scroll',
    props: {
      proType:{
        type:Number,
        default:3
      },
      PullUpLoad:{
        type:Boolean,
        default:true
      },
    },
  data () {
    return {
        scroll:null
    }
  },
  mounted(){
      this.scroll=new bscroll((this.$refs.wrapper),{
          observeDOM:true,
          click:true,
          probeType:this.proType,
          pullUpLoad:this.PullUpLoad
      })  
      if(this.proType===2||this.proType===3){
      this.scroll.on('scroll',(position)=>{
        this.$emit('scroll',position)
      })
      if(this.PullUpLoad){
        this.scroll.on('pullingUp',()=>{
          this.$emit('pullingUp')
        })
      }
    }
  }
}
</script>

<style  scoped>

</style>
