<template>
  <div>
    <p>age: {{ age }}</p>
    <p>company: {{ company }}</p>
    <button @click="changeAge">Change Age</button>
  </div>
</template>

<script setup>
import { ref, onUpdated } from "vue";

const age = ref(1);

const company = ref("Rikkei Academy");
const companies = ["Rikkei Academy", "Rikkei Education", "Rikkei Fukuoka"];

const changeAge = () => {
  age.value = Math.ceil(Math.random() * 10);
};

onUpdated(() => {
  if (age.value < 3) {
    company.value = companies[0];
  } else if (age.value < 7) {
    company.value = companies[1];
  } else {
    company.value = companies[2];
  }
});
</script>

<style>
</style>
