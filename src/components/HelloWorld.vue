<script setup lang="ts">
import { ref } from "vue";
import { animate } from "motion";

const show = ref(true);

function onBeforeEnter(el: Element) {
  animate(el, { transform: "scale(45deg)" }, { duration: 0.5 });
}

function onEnter(el: Element, done: () => void) {
  animate(el, { transform: "rotate(0deg)" }, { duration: 0.5 });
  done();
}
</script>

<template>
  <button @click="show = !show">Toggle</button>

  <Transition @before-enter="onBeforeEnter" @enter="onEnter" :css="false">
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
