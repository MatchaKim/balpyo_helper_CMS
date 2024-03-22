<template>
    <div class="hello">
      <swiper
        :slides-per-view="1"
        :space-between="0"
        :modules="modules"
        @swiper="onSwiper"
        @slideChange="onSlideChange"
        :pagination="{
            dynamicBullets: true,
          }"
      >
        <swiper-slide><MainPromotionCard/></swiper-slide>
        <swiper-slide><OnBoardingCard/></swiper-slide>
        <swiper-slide><OnBoardingCard/></swiper-slide>
        <swiper-slide><OnBoardingCard/></swiper-slide>
        <swiper-slide><OnBoardingCard/></swiper-slide>
        <swiper-slide><OnBoardingCard/></swiper-slide>
      </swiper>
    </div>
  </template>
  
  <script setup>
  import { Navigation,Pagination } from 'swiper';
  import { Swiper, SwiperSlide } from 'swiper/vue';
  
  // Import Swiper styles
  import 'swiper/css';
  import 'swiper/css/navigation';
  
 
      const onSwiper = (swiper) => {
        console.log(swiper);
      };
      const onSlideChange = (swiper) => {
        console.log('slide change');
        console.log(swiper)
      };


  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  .hello{
    width: 100vw;
    height: 100vh;
    background-color: #EB2A63;
  }
  </style>
  