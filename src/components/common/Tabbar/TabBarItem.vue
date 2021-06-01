<template>
    <div class="tabbar-item" @click="itemClick">
        <div v-if="!isActive"><slot name='icon'></slot></div>
        <div v-else><slot name='active-icon'></slot></div>
        <div :class="{active:isActive}"><slot name='text'></slot></div>
    </div>    
   
       
</template>
<script>
export default {
    name:'tarbaritem',
    props:{
        path:String
    },
    methods:{
        itemClick(){
            this.$router.push(this.path).catch(err=>{
            })
        }
    },
    computed:{
        isActive(){
           return this.$route.path.includes(this.path)
        }
    }
}
</script>
<style scoped>
.tabbar-item{
     flex:1;
     text-align: center;
     height: 49px;
     /* line-height: 49px; */
     
  }
    .tabbar-item img{
      width: 24px;
      height: 24px;
      font-size: 14px;
      margin-top:3px ;
      vertical-align: middle;
      margin-bottom: 2px;
  }
  .active{
      color:red;
  }
</style>