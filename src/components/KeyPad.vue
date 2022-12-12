<script setup lang="ts">
// Ref: https://github.com/iamshaunjp/vue-with-typescript
// import type TestProps from "@/types";
import { computed, reactive, ref } from "vue";

export interface IProps {
  title: string;
  initialValue?: number;
}

interface IEmits {
  (event: "click", value: string): void;
}

interface IReactive {
  age: number;
  gender: "male" | "female";
}

// default props - 1
const props = withDefaults(defineProps<IProps>(), {
  title: "Default Title",
  initialValue: 0,
});

// default props - 2
// const { title, initialValue = 0 } = defineProps<Props>();

const emit = defineEmits<IEmits>();

const year = ref<number>(2022);

const person = reactive<IReactive>({ age: 20, gender: "female" });

const displayYear = computed<string>(() => year.value + "年");

function handleInput(event: Event): void {
  const currentValue = (event.target as HTMLInputElement).value;
  console.log("currentValue: ", currentValue);
}
</script>

<template>
  <div class="container">
    <div class="text-green-600 border text-2xl">keypad component</div>
    <input type="text" v-on:input="handleInput" />
    <div>This year: {{ displayYear }}</div>
  </div>
</template>

<style lang="postcss" scoped>
.container {
  @apply border border-blue-500;
}

.test {
  @apply bg-red-200 text-neutral-300 text-2xl text-xl;
}
</style>
