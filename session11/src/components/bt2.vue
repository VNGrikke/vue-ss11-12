<template>
  <div>
    <p>{{ count }}</p>
    <button @click="Counter">tăng</button>
  </div>
</template>

<script setup>
import { onUpdated, ref } from "vue";

const count = ref(0);

onUpdated(() => {
  console.log("count updated", count.value);
});

const Counter = () => {
  count.value++;
};
</script>

<style>
</style>