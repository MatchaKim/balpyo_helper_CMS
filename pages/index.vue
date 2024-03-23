<template>
  <div class="hello" style="position: relative; height: 100vh">
    <div
      style="
        position: absolute;
        padding: 20px 0;
        top: 20px;
        left: 50%;
        transform: translateX(-50%);
        z-index: 100;
        width: 100%;
        display: flex;
        justify-content: center;
        gap: 10px;
      "
    >
      <div
        v-for="index in 4"
        :key="index"
        :class="{
          activated: currentSlide === index,
          inactivated: currentSlide !== index,
        }"
      ></div>
    </div>
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
      <swiper-slide v-for="(item, index) in data" :key="'slide-' + index">
        <OnBoardingCard :mainText="item.mainText" :subText="item.subText" :myPage="index+1" />
      </swiper-slide>
      <swiper-slide><MainPromotionCard /></swiper-slide>
    </swiper>
    <div
      v-if="currentSlide != 4"
      style="
        position: absolute;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        width: 100%;
        padding: 4.5vh 0;
        display: flex;
        justify-content: center;
      "
    >
      <DownLoadButton
      />
    </div>
  </div>
</template>

<script setup>
import { Navigation, Pagination } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";

const currentSlide = ref(1);

const onSwiper = (swiper) => {
  console.log(swiper);
};
const onSlideChange = (swiper) => {
  console.log("slide change");
  console.log("Current slide is: ", swiper.activeIndex + 1);
  currentSlide.value = swiper.activeIndex + 1;
};

const data = [
  {
    mainText: "원하는 시간에 맞춘 대본 생성",
    subText: "원하는 시간에 맞춘 대본 생성",
  },
  {
    mainText: "말의 빠르기에 따른 발표시간 계산",
    subText: "직접 말하지 않아도 발표 시간을 알 수 있어요.",
  },
  {
    mainText: "효율적이고 직관적인 발표연습",
    subText: "대본을 노래방에 온 것처럼 따라 읽기만해도\n자연스럽게 발표연습이 돼요.",
  },
];
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
.hello {
  width: 100%;
  height: 100%;
  background-color: #eb2a63;
}
.activated,
.inactivated {
  transition: background-color 0.3s ease-in-out;
}

.activated {
  width: 21vw;
  height: 2px;
  background-color: white; /* 활성화 상태의 색상 */
  border-radius: 5px;
}

.inactivated {
  width: 21vw;
  height: 2px;
  background-color: #ffffff80; /* 비활성화 상태의 색상 (투명도 포함) */
  border-radius: 5px;
}
</style>
