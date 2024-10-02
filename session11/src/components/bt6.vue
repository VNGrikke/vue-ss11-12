<template>
  <div>
    <p>Count: {{ count }}</p>
    <button @click="increment">Increment</button>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue';

const count = ref(0); 

const increment = () => {
  count.value++;
};

onMounted(() => {
  document.title = `Count: ${count.value}`; 
});

watch(count, (newCount) => {
  document.title = `Count: ${newCount}`;
});
</script>

<style scoped>
</style>
