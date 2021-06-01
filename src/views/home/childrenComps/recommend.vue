<template>
    <div class="recommend">
        <div v-for="(item,index) in recommends" :key="index" class="recommend-items">
            <a :href="item.link">
                <img :src="item.image" alt="">
                <div>{{item.title}}</div>
            </a>
        </div>
    </div>
</template>
<script>
export default {
    name:'recommend',
    props:{
        recommends:{
            type:Array,
            default(){
                return []
            }
        }
    }
}
</script>
<style scoped>
    .recommend{
        display: flex;
        text-align: center;
        font-size:1rem;
        border-bottom:  0.8rem solid #eee;
        padding-bottom: 1.5rem;
        padding-top: 0.5rem;
    }
    .recommend-items{
        flex:1;
        margin: 0.5rem;
        
    }
    .recommend-items img{
        width: 100%;
    }
</style>