<template>
  <div>
    <input type="text" v-model="inputValue" placeholder="Nhập tên cho tab" />
    <p>Giá trị nhập: {{ inputValue }}</p>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from "vue";

const inputValue = ref("");
onMounted(() => {
  document.title = "Nhập tên cho tab";
});

watch(inputValue, (newValue) => {
  document.title = newValue;
});
</script>

<style scoped>
input {
  padding: 8px;
  font-size: 16px;
  margin-bottom: 10px;
}
</style>
