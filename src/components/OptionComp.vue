<script lang="ts">
import { defineComponent } from "vue";

interface IProps {
  title: string;
  initialValue?: number;
}

export default defineComponent({
  props: {
    title: { type: String, required: true },
    initialValue: { type: Number, required: false },
  },
  data() {
    return {
      name: "Rocky",
      weight: 70,
      height: 180,
    };
  },
  computed: {
    userBMI(): number {
      return this.weight / (this.height * 0.01) ** 2;
    },
  },
  methods: {
    handleNameChange(event: Event): void {
      const currentValue = (event.target as HTMLInputElement).value;
      // console.log("currentValue: ", currentValue);
      this.name = currentValue;
    },
    handleExportBMI(): void {
      this.$emit("export", this.userBMI);
    },
  },
});
</script>

<template>
  <div class="container">
    <div class="title">{{ title }}</div>
    <input
      class="input"
      type="text"
      v-on:input="handleNameChange"
      v-bind:value="name"
      placeholder="please input your name"
    />
    <input class="input" type="number" v-model="weight" placeholder="your weight(kg)" />
    <input class="input" type="number" v-model="height" placeholder="height(cm)" />
    <div>{{ name }}'s BMI: {{ userBMI }}</div>
    <button class="button" type="button" v-on:click="handleExportBMI">Export BMI</button>
  </div>
</template>

<style lang="postcss" scoped>
.container {
  @apply border border-green-500 p-5 m-2;
}

.title {
  @apply text-2xl font-bold text-green-500;
}

.input {
  @apply bg-neutral-300 border border-neutral-400 m-2 p-2 rounded;
}

.button {
  @apply bg-neutral-800 text-white p-2 m-2 rounded;
}
</style>
