<script setup>
import { ref, watch, onMounted, onUpdated, onUnmounted } from 'vue';

// State
const count = ref(0);
const inputRef = ref(null);

// Lifecycle Hooks
onMounted(() => {
  console.log("Component mounted!");
  if (inputRef.value) {
    inputRef.value.focus(); // Fokus ke input saat komponen dimuat
  }
});

onUpdated(() => {
  console.log("Component updated!");
});

onUnmounted(() => {
  console.log("Component unmounted!");
});

// Watchers
watch(count, (newValue, oldValue) => {
  console.log(`Count changed from ${oldValue} to ${newValue}`);
});

const increment = () => {
  count.value++;
};
</script>

<template>
  <div>
    <h2>Lifecycle, Template Refs, & Watchers</h2>
    <input ref="inputRef" type="text" placeholder="Focus me on mount" />
    <p>Count: {{ count }}</p>
    <button @click="increment">Increment</button>
  </div>
</template>
