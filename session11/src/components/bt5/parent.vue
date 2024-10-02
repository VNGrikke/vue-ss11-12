<template>
  <div>
    <button @click="toggle">Toggle</button>
    <Child v-show="isShow"></Child>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Child from "./child.vue"

const isShow = ref(false);

const toggle = () => {
  isShow.value = !isShow.value;
};
</script>

<style >
</style>
