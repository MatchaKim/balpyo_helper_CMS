<template>
  <NuxtLayout>
    <NuxtPage/>
  </NuxtLayout>
</template>

<style>
@import "@/assets/css/reset.css";
@font-face {
  font-family: 'Cafe24Moyamoya';
  src: url('./static/Cafe24Moyamoya-Regular-v1.0.woff2') format('woff');
  font-weight: normal;
  font-style: normal;
}
body{
  background-color: #eb2a63;
}



</style>

<script setup>
function setScreenSize() {
  let vh = window.innerHeight * 0.01;

  document.documentElement.style.setProperty('--vh', `${vh}px`);
}

onMounted(()=>{
  setScreenSize()
})
</script>
