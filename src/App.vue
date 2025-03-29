<template>
  <div class="container">
    <h1>Vue.js: Callback, Promises, dan Async/Await</h1>
    
    <button @click="gunakanCallback">Gunakan Callback</button>
    <button @click="gunakanPromise">Gunakan Promise</button>
    <button @click="gunakanAsyncAwait">Gunakan AsyncAwait</button>

    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Klik tombol untuk mulai proses...",
    };
  },
  methods: {
   prosesDataCallback(nama, callback) {
    this.message = `Memproses data untuk $ {nama}...`;
    setTimeout(()=> {
      this.message = `Data ${nama} berhasil
      diproses dengan Callback.`; callback();
    },2000);
   },
   gunakanCallback() {
    this.prosesDataCallback("andi",()=> {
      console.log("proses callback Selesai!");
    });
   },

   prosesDataPromise(nama) {
    return new Promise((resolve)=>{
      this.message = `Memproses data untuk $ {nama}...`;
      setTimeout(()=> {
        this.message = `Data ${nama} Berhasil di proses dengan Promise.`;
        resolve();
      }, 2000);
    });
   },
   gunakanPromise() {
    this.prosesDataPromise("BUDI").then(()=> {
      console.log("proses Promise selesai")
    });
   },

   async prosesDataAsync(nama) {
    this.message = `memproses data untuk $ {nama}...`;
    await new Promise((resolve)=>
  setTimeout(resolve,2000));
  this.message = `Data ${nama} berhasil di proses dengan Asyn/Await.`;
   },
   async gunakanAsyncAwait() {
    await this.prosesDataAsync("citra");
    console.log("proses async/await selesai!");
   }

  }
};
</script>

<style scoped>
.container {
  text-align: center;
  margin-top: 50px;
}
button {
  padding: 10px;
  margin: 5px;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}
button:hover {
  background-color: #0056b3;
}
</style>
