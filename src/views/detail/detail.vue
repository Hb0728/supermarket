<template>
  <div class='detail'>
      <div>{{iid}}</div>
      <h1>huangbinbin</h1>
  </div>
</template>

<script>
export default {
  name: 'detail',
  data(){
    return {
        iid:null
    }
  },
  computed:{},
  components: {},
  created(){},
  mounted(){
      this.iid=this.$route.params.iid
  },
  methods: {}
}
</script>
<style lang='less' scoped>


</style>
