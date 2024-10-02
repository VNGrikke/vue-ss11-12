<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>STT</th>
          <th>Tên sách</th>
          <th>Sinh viên mượn</th>
          <th>Ngày mượn</th>
          <th>Ngày trả</th>
          <th>Trạng thái</th>
          <th>Chức năng</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, index) in users" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ user.borrowedBook }}</td>
          <td>{{ user.name }}</td>
          <td>{{ user.borrowedDate }}</td>
          <td>{{ user.returnDate }}</td>
          <td>
            <select v-model="user.status">
              <option :value="false">Chưa trả</option>
              <option :value="true">Đã trả</option>
            </select>
          </td>
          <td>
            <button @click="$emit('deleteUser', index)">Xoá</button>
            <button @click="$emit('editUser', user)">Sửa</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const props = defineProps(["users"]);
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 25px;
  z-index: 998;
}

th {
  border-bottom: 1px solid rgb(147, 147, 147);
}

th,
td {
  padding: 12px;
  text-align: left;
}

th,
td:first-child {
  text-align: center;
}

td:nth-child(n + 6) {
  text-align: center;
}

th:nth-child(n + 2):nth-child(-n + 5) {
  text-align: left;
}

th:nth-child(2) {
  width: 400px;
}

th:nth-child(n + 4):nth-child(-n + 7) {
  width: 150px;
}

button {
  padding: 8px 12px;
  margin-right: 5px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #0056b3;
}
</style>
