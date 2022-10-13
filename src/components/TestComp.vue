<script setup lang="ts">
import { reactive, ref } from "vue";

const state = reactive({ count: 0 });
const countRef = ref(5566);

// console.log("countRef :>> ", countRef);
// console.log("countRef.value :>> ", countRef.value);

function increment() {
  state.count++;
}

function updateRef() {
  countRef.value = countRef.value + 1;
}
</script>

<template>
  <h1>hello test comp</h1>
  <div>
    <button class="btn" @click="increment">
      {{ state.count }}
    </button>
    <button class="btn" @click="updateRef">update ref</button>
    <div>{{ countRef }}</div>
  </div>
</template>

<style scoped>
.btn {
  margin: 15px;
  padding: 15px;
}
</style>
