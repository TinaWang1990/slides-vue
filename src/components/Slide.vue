<template>
  <div class="silde">

 <img v-bind:src="slide.src" alt="">
  </div>
</template>
<script>
export default {
    data(){
      return {}
    },
    props: ['slide']
}
</script>
<style scoped>
img{
  max-width: 100%;
  height: 200px;
}
.slide{
  display: inline-block;
}
</style>


