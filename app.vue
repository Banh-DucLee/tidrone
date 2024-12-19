<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<style>
  html {
    scroll-behavior: smooth;
  }
  
  body {
    margin: 0 auto;
    padding: 0;
    min-width: var(--width-min);
    max-width: var(--width-max);
    box-sizing: border-box;
  }

  main {
    padding: 75px 0 0 0;
  }

</style>
