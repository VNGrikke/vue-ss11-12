<template>
  <div>dem so: {{ count }}</div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
const count = ref(0);
const time = () => {
  setTimeout(() => {
    count.value++;
    time();
  }, 1000);
};

onMounted(() => {
  time();
});

onUnmounted(() => {
  clearInterval(time);
});
</script>

<style>
</style>