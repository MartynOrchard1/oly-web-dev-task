<template>
  <div class="container">
    <h1>Random Dog Image</h1>

    <img v-if="dogImage" :src="dogImage" alt="Random Dog" class="dog-img" />
    <p v-else>Loading...</p>

    <button @click="fetchDogImage">Get New Dog</button>
    <button @click="saveDogImage" :disabled="!dogImage">Save Dog Image</button>

    <SavedDogs :dogs="savedDogs" @delete="deleteDog" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import SavedDogs from './components/SavedDogs.vue'

const dogImage = ref('')
const savedDogs = ref([])

const fetchDogImage = async () => {
  try {
    const response = await fetch('https://dog.ceo/api/breeds/image/random')
    const data = await response.json()
    dogImage.value = data.message
  } catch (error) {
    console.error('Error fetching dog image:', error)
  }
}

const saveDogImage = () => {
  const name = prompt('Give this dog a name')
  if (name) {
    savedDogs.value.push({ url: dogImage.value, name })
  }
}

onMounted(() => {
  fetchDogImage()
})
</script>

<style scoped>
.container {
  max-width: 700px;
  margin: auto;
  padding: 30px;
  text-align: center;
}

button {
  margin: 10px;
  padding: 10px 20px;
  border: none;
  border-radius: 6px;
  background-color: #1976d2;
  color: white;
  font-size: 14px;
  cursor: pointer;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.dog-img {
  width: 100%;
  border-radius: 12px;
  margin: 20px 0;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.saved-list {
  list-style: none;
  padding: 0;
}

.saved-list li {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

.thumb {
  width: 60px;
  height: 60px;
  border-radius: 6px;
  margin-right: 10px;
  object-fit: cover;
}
</style>