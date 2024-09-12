<script setup>
import { ref } from 'vue'; // Tambahkan ref untuk reactive data

const count = ref(0); // Inisialisasi counter
const boxColor = ref('lightgray'); // Inisialisasi warna box
const currentImageIndex = ref(0); // Inisialisasi index gambar yang tampil saat ini

// Daftar gambar untuk carousel
const images = [
  'https://asset.kompas.com/crops/jzbvIRCoYBVo_Jp9e8vk9U1bdj4=/0x0:1000x667/750x500/data/photo/2023/10/25/653886850f07d.jpg',
  'https://res.cloudinary.com/hello-tickets/image/upload/c_limit,f_auto,q_auto,w_1300/v1689721009/ewegqejis339ztowz6au.jpg',
  'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTw1YEPIWvnIzWldgJX9x0RzyKw63srwfdstw&s'
];

function increment() {
  count.value++; // Fungsi untuk menambah counter
}

function changeColor() {
  // Mengubah warna kotak secara acak
  const colors = ['lightgray', 'lightblue', 'lightgreen', 'lightcoral', 'lightyellow'];
  boxColor.value = colors[Math.floor(Math.random() * colors.length)];
}

function nextImage() {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length; // Pindah ke gambar berikutnya
}

function prevImage() {
  currentImageIndex.value = (currentImageIndex.value - 1 + images.length) % images.length; // Pindah ke gambar sebelumnya
}
</script>

<template>
  <div>
    <!-- Counter Section -->
    <p>Counter: {{ count }}</p>
    <button @click="increment">Tambah</button>
    
    <!-- Box Color Section -->
    <div :style="{ backgroundColor: boxColor, width: '200px', height: '200px', margin: '20px auto' }"></div>
    <button @click="changeColor">Ubah Warna Box</button>
    
    <!-- Image Carousel Section -->
    <div class="carousel">
      <button @click="prevImage">Previous</button>
      <img :src="images[currentImageIndex]" alt="carousel image" />
      <button @click="nextImage">Next</button>
    </div>
  </div>
</template>

<style scoped>
div {
  text-align: center;
  margin-top: 2rem;
}

button {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  cursor: pointer;
}

div > div {
  transition: background-color 0.3s ease;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.carousel img {
  width: 400px;
  height: 200px;
  object-fit: cover;
  margin: 0 10px;
}
</style>