<template>
    <tabbar>
        <tabbaritem path='/home'>
            <img slot='icon' src="~@/assets/img/tabbar/icon01.png" alt="">
            <img slot='active-icon' src="~@/assets/img/tabbar/icon01_active.png" alt="">
            <div slot='text'>首页</div>
        </tabbaritem>
        <tabbaritem path='/category'>
            <img slot='icon' src="~@/assets/img/tabbar/icon02.png" alt="">
            <img slot='active-icon' src="~@/assets/img/tabbar/icon02_active.png" alt="">
            <div slot='text'>分类</div>
        </tabbaritem>
        <tabbaritem path='/cart'>
            <img slot='icon' src="~@/assets/img/tabbar/icon03.png" alt="">
            <img slot='active-icon' src="~@/assets/img/tabbar/icon03_active.png" alt="">
            <div slot='text'>购物车</div>
        </tabbaritem>
        <tabbaritem path='/profile'>
            <img slot='icon' src="~@/assets/img/tabbar/icon04.png" alt="">
            <img slot='active-icon' src="~@/assets/img/tabbar/icon04_active.png" alt="">
            <div slot='text'>我的</div>
        </tabbaritem>
    </tabbar>
</template>
<script>
import tabbar from './Tabbar/Tabbar'
import tabbaritem from './Tabbar/TabBarItem' 
export default {
    name:'maintabbar',
    components:{
        tabbar,
        tabbaritem
    }
}
</script>
<style scoped>

</style>