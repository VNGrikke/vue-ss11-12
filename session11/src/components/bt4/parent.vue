<template>
  <div>
    <p>Age: {{ age }}</p>
    <button @click="increaseAge">Increase age</button>

    <Child :age="age" />
  </div>
</template>

<script setup>
import Child from "./child.vue";

import { ref } from "vue";

const age = ref(1);

const increaseAge = () => {
  age.value++;
};
</script>

<style >
</style>
