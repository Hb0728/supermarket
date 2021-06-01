<template>
  <div class="tab-control">
      <div v-for="(item,index) in titles" :key='index' class="tab-control-item"  @click="itemclick(index)" :class="{active:index===currentIndex}" >
          <span>{{item}}</span>
      </div>
  </div>
</template>

<script>
export default {
    name:"TabControl",
    props:{
        titles:{
            type:Array,
            default(){
                return []
            }
        }
    },
  data () {
    return {
      currentIndex:0
    }
  },
  methods:{
    itemclick(index){
      this.currentIndex=index
      this.$emit('tabclick',index)
    }
  }
}
</script>

<style  scoped>
.tab-control{
  display: flex;
  text-align: center;
}
.tab-control-item{
    flex: 1;
    height: 40px;
		line-height: 40px;
		font-size: 15px;
		background-color: #fff;
}
.active{
  color: pink;
}
.active span {
					border-bottom: 2px solid pink;
					padding: 5px;
				}
</style>
