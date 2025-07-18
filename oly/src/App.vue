<template>
  <div class="container">
    <h1>Random Dog Image 🐶</h1>

    <img v-if="dogImage" :src="dogImage" alt="Random Dog" class="dog-img" />
    <p v-else>Loading...</p>

    <button @click="fetchDogImage">Get New Dog</button>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const dogImage = ref('')

const fetchDogImage = async () => {
  try {
    const response = await fetch('https://dog.ceo/api/breeds/image/random/3')
    const data = await response.json()
    dogImage.value = data.message
  } catch (error) {
    console.error('Error fetching dog image:', error)
  }
}

onMounted(() => {
  fetchDogImage()
})
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 50px auto;
  text-align: center;
  font-family: 'Arial', sans-serif;
}

button {
  margin-top: 20px;
  padding: 10px 16px;
  font-size: 16px;
  background-color: #1976d2;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background-color: #1565c0;
}

.dog-img {
  width: 100%;
  border-radius: 12px;
  margin-top: 20px;
}
</style>
