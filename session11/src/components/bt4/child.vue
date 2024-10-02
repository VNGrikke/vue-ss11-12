<template>
  <div>
    <p>Received Age: {{ props.age }}</p>
  </div>
</template>

<script setup>
const props = defineProps(["age"]);

import { onUpdated } from 'vue';

onUpdated(() => {
  alert('Giá trị của biến age đã thay đổi');
});
</script>

<style >
</style>
