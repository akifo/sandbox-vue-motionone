<script setup lang="ts">
import { ref } from "vue";
import { animate } from "motion";

const show = ref(true);

async function onEnter(el: Element, done: () => void) {
  await animate(
    el,
    { transform: ["rotate(90deg)", "translateX(100px) rotate(45deg)", "none"] },
    { duration: 2.5 }
  ).finished;
  console.log("onEnter finished");
  done();
}
</script>

<template>
  <button @click="show = !show">Toggle</button>

  <Transition @enter="onEnter" :css="false">
    <div class="gsap-box" v-if="show"></div>
  </Transition>
</template>

<style scoped>
.gsap-box {
  background: #42b883;
  margin-top: 20px;
  width: 30px;
  height: 30px;
}
</style>
