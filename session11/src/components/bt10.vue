<template>
  <div>
    <h1>thoi gian hien tai: {{ hours }}:{{ minutes }}:{{ seconds }}</h1>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

const getCurrentTime = () => {
  const now = new Date();
  hours.value = now.getHours();
  minutes.value = now.getMinutes();
  seconds.value = now.getSeconds();
};

onMounted(() => {
  getCurrentTime();
  setInterval(getCurrentTime, 1000);
});

</script>

<style>
</style>
