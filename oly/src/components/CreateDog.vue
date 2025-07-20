<template>
  <div class="form-container">
    <h2>Create Your Own Dog</h2>
    <form @submit.prevent="handleSubmit">
      <label for="name">Dog Name</label>
      <input type="text" id="name" v-model="name" required />

      <label for="url">Image URL</label>
      <input type="url" id="url" v-model="url" required />

      <button type="submit">Add Dog</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add'])
const name = ref('')
const url = ref('')

const handleSubmit = () => {
    emit('add', { name: name.value, url: url.value })

    // Reset the form
    name.value = ''
    url.value = ''
}
</script>

<style scoped>
.form-container {
  max-width: 400px;
  margin: 30px auto;
  padding: 20px;
  background: #f9f9f9;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  color: black;
}

form {
  display: flex;
  flex-direction: column;
  gap: 12px;
  color: black;
}

input {
  padding: 10px;
  border-radius: 6px;
  border: 1px solid #ccc;
}

button {
  padding: 10px;
  background-color: #388e3c;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background-color: #2e7d32;
}
</style>