<template>
  <div class="good">
  <goodslistitem v-for="(item,index) in goods" :key='index' :goods-item='item' ></goodslistitem>
  </div>
</template>

<script>
import goodslistitem from './goodslistitem'
export default {
    name:"goods",
    components:{
        goodslistitem
    },
    props:{
        goods:{
            type:Array,
            default(){
                return []
            }  
        }
    },
    data () {
        return {
            currentindex:0
        }
    },
    methods:{
    }
}
</script>

<style  scoped>
    .good{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }
</style>
