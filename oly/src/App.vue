<template>
  <div class="container">
    <h1>Random Dog Image</h1>

    <img v-if="dogImage" :src="dogImage" alt="Random Dog" class="dog-img" />
    <p v-else>Loading...</p>

    <button @click="fetchDogImage">Get New Dog</button>
    <button @click="saveDogImage" :disabled="!dogImage">Save Dog Image</button>

    <h2>Saved Dogs:</h2>
    <ul class="saved-list">
      <li v-for="(dog, index) in savedDogs" :key="index">
        <img :src="dog.url" alt="Dog image" class="thumb">
        <span>{{ dog.name }}</span>
      </li>
    </ul>
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

<style scoped>
.container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  text-align: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f9f9f9;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba( 0, 0, 0, 0.1);
}

h1 {
  color: #333;
  margin-bottom: 20px;
}

button {
  margin-top: 20px;
  padding: 12px 20px;
  font-size: 16px;
  background-color: #1976d2;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #135ba1;
}

.dog-img {
  width: 100%;
  height: auto;
  border-radius: 12px;
  margin-top: 20px;
  object-fit: cover;
  box-shadow: 0 4px 15px rgba( 0, 0, 0, 0.2);
}

@media (max-width: 600px) {
  h1 {
    font-size: 22px;
  }

  button {
    font-size: 14px;
    padding: 10px 16px;
  }
}
</style>
