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