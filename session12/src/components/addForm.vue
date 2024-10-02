<template>
  <form @submit.prevent="handleSubmit">
    <header>
      <h2>
        {{ user ? "Sửa thông tin mượn sách" : "Thêm thông tin mượn sách" }}
      </h2>
      <p @click="closeForm" class="close-button">x</p>
    </header>
    <div class="form-body">
      <input
        type="text"
        v-model="borrowedBook"
        placeholder="Tên sách"
        required
      />
      <input type="text" v-model="name" placeholder="Tên người mượn" required />
      <input
        type="date"
        v-model="borrowedDate"
        placeholder="Ngày mượn"
        required
      />
      <input type="date" v-model="returnDate" placeholder="Ngày trả" />
    </div>
    <button type="submit" class="submit-button">
      {{ user ? "Cập nhật" : "Thêm mới" }}
    </button>
  </form>
</template>

<script setup>
import { ref, watch, onMounted } from "vue";

const props = defineProps(["user"]);
const emit = defineEmits(["close", "saveUser"]);

const borrowedBook = ref("");
const name = ref("");
const borrowedDate = ref("");
const returnDate = ref("");

onMounted(() => {
  if (props.user) {
    borrowedBook.value = props.user.borrowedBook;
    name.value = props.user.name;
    borrowedDate.value = props.user.borrowedDate;
    returnDate.value = props.user.returnDate;
  }
});

const handleSubmit = () => {
  const newUser = {
    borrowedBook: borrowedBook.value,
    name: name.value,
    borrowedDate: borrowedDate.value,
    returnDate: returnDate.value,
    status: props.user ? props.user.status : false,
  };

  emit("saveUser", newUser);
};

const closeForm = () => {
  emit("close");
};
</script>

<style scoped>
form {
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: auto;
  background-color: #ffffff;
  border-radius: 8px;
  padding: 20px;
  max-width: 400px;
  margin: 20px auto;
  top: 170px;
  left: 37%;
  z-index: 999;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  width: 100%;
}

h2 {
  color: #333;
  font-size: 1.5rem;
}

.close-button {
  cursor: pointer;
  color: #ff4d4d;
  font-size: 1.2rem;
}

.form-body {
  display: flex;
  flex-direction: column;
  gap: 15px;
  width: 100%;
}

input[type="text"],
input[type="date"] {
  padding: 10px;
  border: 1px solid #cccccc;
  border-radius: 4px;
  width: 100%;
  font-size: 1rem;
  transition: border-color 0.3s;
}

input[type="text"]:focus,
input[type="date"]:focus {
  border-color: #007bff;
  outline: none;
}

.submit-button {
  padding: 10px 126px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
  margin-top: 20px;
}

.submit-button:hover {
  background-color: #0056b3;
}
</style>
