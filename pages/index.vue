<template>
    <ConfettiExplosion v-if="currentSlide==4" />
  <div class="hello" style="position: relative; height: calc(var(--vh, 1vh) * 100)">
    <div
      style="
        position: absolute;
        padding: 15px 0;
        top: 6vh;
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

      <!-- <div
        style="
          position: absolute;
          top: 40vh;
          left: 50%;
          transform: translateX(-50%);
          z-index: 100;
          width: 100vw;
          display: flex;
          justify-content: space-between;
          gap: 10px;
        "
      >
        <div>
          <img src="/static/next icon inactivated.png" style="height: 8vh; pointer-events: none;" v-if="currentSlide==1"/>
          <img src="/static/next icon.png" style="height: 8vh; pointer-events: none; transform: rotate(180deg)" v-else />
        </div>
        <div>
          <img src="/static/next icon inactivated.png" style="height: 8vh; pointer-events: none; transform: rotate(180deg)" v-if="currentSlide==4"/>
          <img src="/static/next icon.png" style="height: 8vh; pointer-events: none;" v-else />
        </div>
      </div> -->
    </div>
    <swiper
      style="width: 100vw"
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
        <OnBoardingCard
          :mainText="item.mainText"
          :subText="item.subText"
          :myPage="index + 1"
        />
      </swiper-slide>
      <swiper-slide><MainPromotionCard /></swiper-slide>
    </swiper>
    <div :class="{ 'download-button-container': true, active: currentSlide >= 4 }" >
      <DownLoadButton v-if="isAndroid" @click="download()" />
      <WelcomeButton v-else/>
    </div>
  </div>
</template>

<script setup>
import { Navigation, Pagination } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import ConfettiExplosion from "vue-confetti-explosion";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import WelcomeButton from "~/components/WelcomeButton.vue";

const currentSlide = ref(1);
const isAndroid = ref(false);

function download() {
  console.log("down")
 window.location.href = "https://balpyo-bucket.s3.ap-northeast-2.amazonaws.com/balpyo.site.apk";
}


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
const checkAndroid = () => {
  const userAgent = window.navigator.userAgent;
  isAndroid.value = /Android/i.test(userAgent);
};

onMounted(() => {
  checkAndroid();
 
});
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
}
.activated,
.inactivated {
  transition: background-color 0.3s ease-in-out;
}

.activated {
  width: 21vw;
  height: 2px;
  background-color: white;
  border-radius: 5px;
}

.inactivated {
  width: 21vw;
  height: 2px;
  background-color: #ffffff80;
  border-radius: 5px;
}

.download-button-container {
  visibility: hidden;
  opacity: 0;
  transform: translateY(100%);
  transition: all 0.6s ease-in;
  position: absolute;
  bottom: 40%;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  padding: 0 0 0 0;
  display: flex;
  justify-content: center;
  z-index: 1000;
}

.download-button-container.active {
  visibility: visible;
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}
</style>
