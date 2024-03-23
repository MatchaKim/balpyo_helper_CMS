<template>
    <div   style="
      height:100vh;
      width: 100vw;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    ">
  <div
    style="
      height: 100vh;
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
      "
    >
    <img :src="imagePath" style="height: 55vh; padding-bottom: 35px" />
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
  imagePath.value = "../static/"+props.myPage+".png";
  console.log("imagePath.value"+imagePath.value)
});

</script>

<style scoped></style>
