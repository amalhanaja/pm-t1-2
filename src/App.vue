<script setup lang="ts">
import GreetingComponent from "@/components/GreetingComponent.vue";
import { onMounted, ref } from "vue";
const count = ref(50);

const startCountDown = () => {
  count.value = 50;
  const interval = setInterval(() => {
    count.value--;
    if (count.value < 0) clearInterval(interval);
  }, 1000);
};

onMounted(() => {
  startCountDown();
});
</script>

<template>
  <main>
    <GreetingComponent></GreetingComponent>
    <div class="count-down">
      <div v-if="count > 0">
        <h4>Hitungan Mundur</h4>
        <div class="counter">{{ count }}</div>
      </div>
      <button v-if="count <= 0" @click="startCountDown">
        Mulai Hitung Mundur
      </button>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.count-down {
  padding: 1rem;
  background-color: #153131;
  border-radius: 16px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2);
  color: white;
}

h4 {
  padding: 0;
  margin-top: 0;
  margin-bottom: 0.5rem;
}
.counter {
  text-align: center;
}
</style>
