<template>
  <div
    style="
      height: height: calc(var(--vh, 1vh) * 100);
      width: 100vw;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    "
  >
    <div
      style="
        padding-top:12vh;
        width: 100vw;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
      "
    >
      <Header :mainText="mainTextProc" :subText="subTextProc" />
      <div
        style="
          width: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;
          height:100%;
        "
      >
        <img :src="imagePath" style="height: 70vh;" />
      </div>
    </div>
  </div>
</template>
<script setup>
const mainTextProc = ref("");
const subTextProc = ref("");
const props = defineProps({
  mainText: String,
  subText: String,
  myPage: Number,
});
const imagePath = computed(() => `/static/${props.myPage}.png`);

onBeforeMount(() => {
  mainTextProc.value = props.mainText;
  subTextProc.value = props.subText;
  console.log(props.myPage);
  imagePath.value = "../static/" + props.myPage + ".png";
  console.log("imagePath.value" + imagePath.value);
});
</script>

<style scoped></style>
