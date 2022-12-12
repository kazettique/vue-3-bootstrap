<script setup lang="ts">
// Ref: https://github.com/iamshaunjp/vue-with-typescript
// import type TestProps from "@/types";
import { computed, reactive, ref } from "vue";

export interface IProps {
  title: string;
  initialValue?: number;
}

interface IEmits {
  (event: "export", value: number): void;
}

interface IReactive {
  name: string;
  weight: number;
  height: number;
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

const person = reactive<IReactive>({
  name: "Rocky",
  weight: 70,
  height: 180,
});

const userBMI = computed<number>(() => person.weight / (person.height * 0.01) ** 2);

function handleExportBMI() {
  emit("export", userBMI.value);
}

function handleNameChange(event: Event): void {
  const currentValue = (event.target as HTMLInputElement).value;
  // console.log("currentValue: ", currentValue);
  person.name = currentValue;
}
</script>

<template>
  <div class="container">
    <div class="title">{{ props.title }}</div>
    <input
      class="input"
      type="text"
      v-on:input="handleNameChange"
      v-bind:value="person.name"
      placeholder="please input your name"
    />
    <input
      class="input"
      type="number"
      v-model="person.weight"
      placeholder="your weight(kg)"
    />
    <input class="input" type="number" v-model="person.height" placeholder="height(cm)" />
    <div>{{ person.name }}'s BMI: {{ userBMI }}</div>
    <button class="button" type="button" v-on:click="handleExportBMI">Export BMI</button>
  </div>
</template>

<style lang="postcss" scoped>
.container {
  @apply border border-blue-500 p-5 m-2;
}

.title {
  @apply text-2xl font-bold text-blue-500;
}

.input {
  @apply bg-neutral-300 border border-neutral-400 m-2 p-2 rounded;
}

.button {
  @apply bg-neutral-800 text-white p-2 m-2 rounded;
}
</style>
