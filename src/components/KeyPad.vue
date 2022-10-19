<script setup lang="ts">
import { computed, reactive, ref, Ref } from "vue";

interface IProps {
  title: string;
  initialValue?: number;
}

interface IEmits {
  (event: "click", value: string): void;
}

interface IRef {
  year: number;
}

interface IReactive {
  age: number;
  gender: "male" | "female";
}

// default props - 1
const props = withDefaults(defineProps<IProps>(), {
  title: "Default Title",
  intialValue: 0,
});

// default props - 2
// const { title, initialValue = 0 } = defineProps<Props>();

const emit = defineEmits<IEmits>();

const year: Ref<IRef> = ref(2022);

const person: IReactive = reactive({ age: 20, gender: "female" });

const displayYear = computed<string>(() => year.value + "年");

function handleChange(event) {
  const currentValue = (event.target as HTMLInputElement).value;
  console.log("currentValue: ", currentValue);
}
</script>

<template>
  <div>keypad componenet</div>
  <input type="text" v-on:change="handleChange" />
</template>

<style scoped></style>
