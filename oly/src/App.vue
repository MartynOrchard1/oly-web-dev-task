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
    const response = await fetch('https://dog.ceo/api/breeds/image/random')
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

