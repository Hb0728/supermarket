<template>
  <div id="home">
    <navbar class="home-nav"><div slot="center">购物街</div></navbar>
    <bscroll class="content" :proType="3" ref="scroll" @scroll="getposition" :pull-up-load="true" @pullingUp="loadmore">
      <home-swiper :banners="banners"></home-swiper>
      <recommend :recommends='recommends'></recommend>
      <feature></feature>
      <tab-control class="tab-control" :titles="['流行','新款','精选']" @tabclick='tabclick'></tab-control>
      <goods-list :goods="goods[item].list"></goods-list>
    </bscroll>
    <backtop @click.native="clickbacktop" v-show="isshowbacktop"></backtop>
  </div>
</template>

<script>
import HomeSwiper from './childrenComps/HomeSwiper'
import recommend from './childrenComps/recommend'
import Feature from './childrenComps/FeatureView'

import TabControl from '../../components/content/tabControl/TabControl'
import navbar from '../../components/common/navbar/NavBar'
import GoodsList from '../../components/content/goods/goodslist'
import bscroll from '../../components/common/better-scroll/scroll'
import backtop from '../../components/content/backtop/backtop'

import {getHomeMultidata,getHomeGoods} from '../../network/home'
export default {
  name:'Home',
  data(){
    return{
      banners:[],
      recommends:[],
      goods:{
        'pop':{page:0,list:[]},
        'new':{page:0,list:[]},
        'sell':{page:0,list:[]}
      },
      item:"pop",
      isshowbacktop:false,
    }
  },
  components: {
    navbar,
    HomeSwiper,
    recommend,
    Feature,
    TabControl,
    GoodsList,
    bscroll,
    backtop,
  },
  created(){
    this.gethomemultidata()
    this.gethomegoods('pop')
    this.gethomegoods('new')
    this.gethomegoods('sell')
    
  },
  mounted(){
    this.$bus.$on('imageload',
    this.debounce(this.$refs.scroll.refresh
    ,500),
    )

  },
  methods:{
    gethomemultidata(){
      getHomeMultidata().then(res=>{
      this.banners=res.data.banner.list;
      this.recommends=res.data.recommend.list;
      })
    },
    gethomegoods(type){
      let page=this.goods[type].page+1
      getHomeGoods(type,page).then(res=>{
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page += 1;
        console.log(this.goods[type].list);
      })
      },
      tabclick(index){
        if(index==0){
          this.item='pop'
        }else if(index==1){
          this.item='new'
        }else if(index==2){
          this.item='sell'
        }
    },
    clickbacktop(){
      this.$refs.scroll.scroll.scrollTo(0,0);
    },
    getposition(position){
      if(-position.y > 500){
        this.isshowbacktop=true
      }else{
       this.isshowbacktop=false
      }
    },
    /**
     *降频函数
     *这个 debounce 函数在给定的时间间隔内只允许你提供的回调函数执行一次，以此降低它的执行频率。
     *调用:	debounce(function() {}, 250) 
     * @param {*} func回调函数
     * @param {*} wait等待时间,推荐250
     * @param {*} immediate
     * @returns
     */
    debounce(func, wait){
      let timer =null
      return function (){
        if(timer!==null){
        clearTimeout(timer)
      }
      timer = setTimeout(func
      , wait);
      }
    },
    loadmore(){
      this.gethomegoods(this.item)
      this.$refs.scroll.scroll.finishPullUp()
      console.log(this.item);
    }
  }
}
</script>
<style scoped>
  #home{
    padding-top: 2.75rem;
    height: 90vh;
  }
  .home-nav{
    background-color: pink;
    color:#fff;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }
  .tab-control{
    position: sticky;
    top:44px;
    z-index: 9;
  }
  .content{
    height: 100%;
    overflow: hidden;
  }
</style>