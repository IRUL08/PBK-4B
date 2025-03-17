<script setup>
import { ref } from 'vue';

// 1. Membuat variabel reaktif dengan "ref"
const message = ref('Hello Vue!');
const isVisible = ref(true);
const inputText = ref('');
const count = ref(0);

// 4. Menggunakan syntax Event Listener
const increment = () => {
  count.value++;
};
</script>

<template>
  <div>
    <!-- 2. Menggunakan syntax text interpolation -->
    <h1>{{ message }}</h1>

    <!-- 6. Menggunakan Conditional Rendering -->
    <button @click="isVisible = !isVisible">Toggle Teks</button>
    <p v-if="isVisible">Teks ini bisa disembunyikan</p>

    <!-- 3. Menggunakan syntax Form Binding -->
    <input v-model="inputText" placeholder="Ketik sesuatu..." />
    <p>Isi input: {{ inputText }}</p>

    <!-- 4. Menggunakan Event Listener -->
    <button @click="increment">Tambah</button>
    <p>Hitungan: {{ count }}</p>

    <!-- 5. Menggunakan Attribute Binding -->
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>
