<script setup>
import { ref, computed } from 'vue'
const carName = ref("");

const cars = ref([
  { id: 1, name: "Toyota Avanza", sold: true },
  { id: 2, name: "Honda Civic", sold: false },
  { id: 3, name: "Suzuki Ertiga", sold: false },
  { id: 4, name: "Mitsubishi Xpander", sold: false },
  { id: 5, name: "Nissan Livina", sold: false },
]);

const addCar = () => {
  let newCar = {
    id: cars.value.length + 1,
    name: carName.value,
    sold: false,
  };

  cars.value.push(newCar);
  carName.value = "";
};

const soldCars = computed(() => {
    return cars.value.filter((car) => car.sold == true)
})

const availableCars = computed(() => {
    return cars.value.filter((car) => car.sold == false)
})
</script>

<template>
  <div class="container">
    <h1>Sistem Penjualan Mobil</h1>

    <div class="input-section">
      <input v-model="carName" placeholder="Masukkan nama mobil" />
      <button @click="addCar">Tambah Mobil</button>
    </div>

    <h2>Daftar Semua Mobil</h2>
    <ul class="car-list">
      <li v-for="car in cars" :key="car.id" class="car-item"> 
        {{ car.id }}. {{ car.name }} - <span :class="{'sold': car.sold}">{{ car.sold ? 'Terjual' : 'Tersedia' }}</span>
        <input type="checkbox" v-model="car.sold"/>
      </li>
    </ul>

    <h2>Mobil Terjual</h2>
    <ul class="car-list">
      <li v-for="car in soldCars" :key="car.id" class="car-item"> 
        {{ car.id }}. {{ car.name }} - <span class="sold">Terjual</span>
        <input type="checkbox" v-model="car.sold"/>
      </li>
    </ul>

    <h2>Mobil Tersedia</h2>
    <ul class="car-list">
      <li v-for="car in availableCars" :key="car.id" class="car-item"> 
        {{ car.id }}. {{ car.name }} - <span class="available">Tersedia</span>
        <input type="checkbox" v-model="car.sold"/>
      </li>
    </ul>
  </div>
</template>

<style>
.container {
  max-width: 600px;
  margin: auto;
  text-align: center;
  font-family: Arial, sans-serif;
}

.input-section {
  margin-bottom: 20px;
}

input {
  padding: 8px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px 12px;
  background-color: #28a745;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #218838;
}

.car-list {
  list-style-type: none;
  padding: 0;
}

.car-item {
  background: #f8f9fa;
  padding: 10px;
  margin: 5px 0;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sold {
  color: red;
  font-weight: bold;
}

.available {
  color: green;
  font-weight: bold;
}
</style>
