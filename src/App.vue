<template>
  <div id="app">
    <router-view/>
    <maintabbar></maintabbar>
  </div>
</template>
<script>
import maintabbar from './components/common/MainTabBar'
export default {
  name:'App',
  components:{
    maintabbar
  }
}
</script>
<style>
@import './assets/css/base.css';
</style>
