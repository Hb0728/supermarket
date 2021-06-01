<template>
  <div class="box">
      <div class="back-top">
          <img src="../../../assets/img/back-top.png" alt="">
      </div>
  </div>
</template>

<script>
export default {
    name:'backTop',
  data () {
    return {
    }
  }
}
</script>

<style  scoped>
.box{
    position: relative;
}
.back-top{
    position: fixed;
    right: 1em;
    bottom: 3em;
    z-index: 1000;
}
.back-top img{
    width: 3em;
    height: 3em;
}

</style>
