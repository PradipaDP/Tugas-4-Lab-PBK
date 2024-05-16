<template>
  <button @click="handleClick" :class="{ zero: value === '0' }">
    {{ value }}
  </button>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  value: String,
});

const emit = defineEmits(["click"]);

const handleClick = () => {
  emit("click", props.value);
};
</script>

<style scoped>
button {
  width: 50px;
  height: 50px;
  font-size: 1.2em;
  margin: 5px;
}
button.zero {
  grid-column: span 2;
}
</style>
