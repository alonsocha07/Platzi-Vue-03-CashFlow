<template>
  <Suspense>
    <template #default>
      <Home></Home>
    </template>
    <template #fallback>
      <Splashscreen></Splashscreen>
    </template>
  </Suspense>
</template>

<script setup>
 import Splashscreen from "./components/SplashScreen.vue";

import { defineAsyncComponent } from 'vue';

const Home = defineAsyncComponent(() => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(import("./components/Home.vue"))
    }, 2500)
  })
})
</script>

<style >
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
