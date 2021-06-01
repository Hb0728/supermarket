<template>
  <div class="wrapper" ref="wrapper">
      <div class="content">
          <slot></slot>
      </div>
  </div>
</template>

<script>
import bscroll from 'better-scroll'
export default {
    name:'scroll',
    props:{
      proType:{
        type:Number,
        default:3
      }
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
          probeType:this.proType
      })  
      if(this.proType===2||this.proType===3){
      this.scroll.on('scroll',(position)=>{
        this.$emit('scroll',position)
      })
    }
  }
}
</script>

<style  scoped>

</style>
