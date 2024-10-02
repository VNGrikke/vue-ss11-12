<template>
  <div>
    <header>
      <h2>Quản lý mượn trả sách</h2>
      <button @click="addUser" class="btn-add">Thêm thông tin</button>
    </header>
    <Table :show="isShow" :users="users" @editUser="editUser" @deleteUser="deleteUser"/>
    <Addform v-if="isShow" @close="isShow = false" :user="selectedUser" @saveUser="saveUser"/>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Table from "./components/table.vue";
import Addform from "./components/addForm.vue";

const isShow = ref(false);
const users = ref(JSON.parse(localStorage.getItem("users")) || []);
const selectedUser = ref(null);

const addUser = () => {
  selectedUser.value = null;
  isShow.value = true;
};

const editUser = (user) => {
  selectedUser.value = { ...user };
  isShow.value = true;
};

const saveUser = (userData) => {
  if (selectedUser.value) {
    const index = users.value.findIndex(
      (u) => u.name === selectedUser.value.name
    );
    if (index !== -1) users.value[index] = userData;
  } else {
    users.value.push(userData);
  }
  localStorage.setItem("users", JSON.stringify(users.value));
  isShow.value = false;
};

const deleteUser = (index) => {
  users.value.splice(index, 1);
  localStorage.setItem("users", JSON.stringify(users.value));
};
</script>

<style>
header {
  display: flex;
  background-color: #f1f1f1;
  text-align: center;
  justify-content: space-between;
  width: 100%;
}
.btn-add {
  background-color: #4caf50;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  float: right;
  margin-top: 10px;
  margin-right: 10px;
  transition: background-color 0.3s;
  border-radius: 4px;
}
</style>
