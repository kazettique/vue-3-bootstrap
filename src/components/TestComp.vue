<script setup lang="ts">
import { computed, reactive, ref } from "vue";

const state = reactive<{ count: number }>({ count: 0 });
const countRef = ref<number>(5566);

// update state
function increment(): void {
  state.count++;
}

// update ref
function updateRef(): void {
  countRef.value = countRef.value + 1;
}

// computed - 1: with computed caching
const isOdd = computed<boolean>(() => state.count % 2 === 1);

// computed - 2: without computed caching
function isOdd2(): boolean {
  return state.count % 2 === 1;
}
</script>

<template>
  <h1>hello test comp</h1>
  <div>
    <button class="btn" @click="increment">
      {{ state.count }}
    </button>
    <div>isOdd: {{ isOdd }}</div>
    <div>isOdd2: {{ isOdd2() }}</div>
  </div>
  <div>
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
