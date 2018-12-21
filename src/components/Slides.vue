<template>
  <div class="slides">
    <div class="slides-inner" v-bind:style="{width: innerWidth+'px', marginLeft:'-'+slidesInnerMarginLeft+'px'}">
        <Slide v-for="slide in slides" :key="slide.id" v-bind:slide="slide" v-bind:style="{width: singleWidth+'px'}" style=" display: inline-block;"></Slide>
    </div>

    <div class="nav">
      <span v-on:click="gotopre">Pre</span>
      <span class="nav-number" v-for="slide in slides" :key="slide.id">{{slide.id}}</span>
      <span v-on:click="gotonext">next</span>
    </div>
  </div>
</template>
<script>
import Slide from './Slide';
export default {
  data: () => ({
      slides: [
        {id:1, src: "https://cdn.pastemagazine.com/www/articles/GrinchPOster_header.jpg"},
        {id:2, src: "https://cdn.newsapi.com.au/image/v1/9fdbf585d17c95f7a31ccacdb6466af9"},
        {id:3, src: "https://media.gettyimages.com/photos/butterfly-at-sunset-picture-id507031708?s=612x612"},
        {id:4, src: "http://i.huffpost.com/gen/1202507/thumbs/o-FIRST-DAY-OF-SUMMER-facebook.jpg"},
        {id:5, src: "https://image.apost.com/media/articletranslation/2018/07/25/15/5869f3b9bf24aa3d0205d1513f3a3838_500x1.jpg"}
      ],
      innerWidth: 0,
      singleWidth: 0,
      currentIndex: 0
  }),
  components: {
    Slide
  },
  computed: {
    slidesInnerMarginLeft (){
      return this.currentIndex*this.singleWidth
    }
  },
  methods: {
    gotopre(){
      if(this.currentIndex ===0){
        return
      }
      this.currentIndex--
    },
    gotonext(){
      if(this.currentIndex === this.slides.length -1){
        return
      }
      this.currentIndex++
    }
  },
  props: {
    itemsPerSlide: {
      type: null,
      default: 2
    }
  },
  mounted: function() {
    let singleWidth = this.$el.clientWidth/this.itemsPerSlide
    this.singleWidth = singleWidth
    this.innerWidth = singleWidth*this.slides.length

  }
}
</script>
<style scoped>
.slides-inner{
  width: 2500px;
  display: block;
}
.slides{
  overflow: hidden;
}
</style>


