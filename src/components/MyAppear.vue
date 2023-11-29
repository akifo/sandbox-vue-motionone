<script lang="ts" setup>
import { ref } from "vue";

const showWelcomeMessage = ref(true);
</script>

<template>
  <button @click="showWelcomeMessage = !showWelcomeMessage">
    Toggle Welcome Message
  </button>
  <transition appear>
    <div v-if="showWelcomeMessage">Welcome to our website!</div>
  </transition>
</template>

<style scoped>
/* トランジションの開始状態 */
.v-enter-from,
.v-appear-from {
  opacity: 0;
  transform: translateY(-10px);
}

/* トランジションの終了状態 */
.v-enter-to,
.v-appear-to {
  opacity: 1;
  transform: translateY(0);
}

/* トランジションの期間 */
.v-enter-active,
.v-appear-active {
  transition: opacity 1.5s, transform 1.5s;
}
</style>
