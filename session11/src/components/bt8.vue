<template>
  <div>
    <h1>chieu rong cua so: {{ windowWidth }}px</h1>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const windowWidth = ref(window.innerWidth);

const updateWidth = () => {
  windowWidth.value = window.innerWidth;
};

onMounted(() => {
  window.addEventListener("resize", updateWidth);
});

onUnmounted(() => {
  window.removeEventListener("resize", updateWidth);
});
</script>

<style>

</style>
