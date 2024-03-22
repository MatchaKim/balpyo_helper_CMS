<template>
    <div>
      <slot />
    </div>
</template>

<style>


  @font-face {
    font-family: 'Pretendard';
    src: url('./assets/Pretendard-Regular.woff2') format('woff2');
    font-weight: 400; /* Normal */
    font-style: normal;
  }
  
  @font-face {
    font-family: 'Pretendard';
    src: url('./assets/Pretendard-Medium.woff2') format('woff2');
    font-weight: 500; /* Medium */
    font-style: normal;
  }
  
  @font-face {
    font-family: 'Pretendard';
    src: url('./assets/Pretendard-SemiBold.woff2') format('woff2');
    font-weight: 600; /* SemiBold */
    font-style: normal;
  }
  
  @font-face {
    font-family: 'Pretendard';
    src: url('./assets/Pretendard-Bold.woff2') format('woff2');
    font-weight: 700; /* Bold */
    font-style: normal;
  }
  
  @font-face {
    font-family: 'Pretendard';
    src: url('./assets/Pretendard-ExtraBold.woff2') format('woff2');
    font-weight: 800; /* ExtraBold */
    font-style: normal;
  }
  
  
  body {
    font-family: 'Pretendard', sans-serif;
  }
</style>