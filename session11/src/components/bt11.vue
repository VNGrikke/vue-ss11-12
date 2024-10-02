<template>
  <div>
    <div class="light red">
      <p v-show="redLight.show">{{ redLight.time }}</p>
    </div>
    <div class="light green">
      <p v-show="greenLight.show">{{ greenLight.time }}</p>
    </div>
    <div class="light orange">
      <p v-show="orangeLight.show">{{ orangeLight.time }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const redLight = ref({
  show: false,
  time: 40,
  originalTime: 40,
});

const greenLight = ref({
  show: false,
  time: 60,
  originalTime: 60,
});

const orangeLight = ref({
  show: false,
  time: 3,
  originalTime: 3,
});

const startCountdown = (light, callback) => {
  light.show = true;
  // setInterval là một hàm trong JavaScript được sử dụng để thực thi một hàm hoặc một đoạn mã nhất định
  // sau mỗi khoảng thời gian xác định (tính bằng mili giây) một cách liên tục cho đến khi nó được dừng lại
  // bằng clearInterval. Đây là một cách hữu ích để lập lịch cho các tác vụ định kỳ trong ứng dụng.
  const countdown = setInterval(() => {
    if (light.time > 0) {
      light.time--;
    } else {
      clearInterval(countdown);
      light.show = false;
      light.time = light.originalTime;
      if (callback) {
        callback();
      }
    }
  }, 1000);
};

const switchLights = () => {
  startCountdown(redLight.value, () => {
    startCountdown(greenLight.value, () => {
      startCountdown(orangeLight.value, () => {
        switchLights();
      });
    });
  });
};

onMounted(() => {
  switchLights();
});
</script>

<style>
p {
  font-size: 2rem;
  font-weight: bold;
  text-align: center;
}

.light {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
}

.red {
  background-color: red;
}

.green {
  background-color: green;
}

.orange {
  background-color: orange;
}
</style>
