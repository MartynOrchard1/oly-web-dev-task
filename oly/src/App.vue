<template>
  <div class="container">
    <h1>Random Dog Image 🐶</h1>

    <img v-if="dogImage" :src="dogImage" alt="Random Dog" class="dog-img" />
    <p v-else>Loading...</p>

    <button @click="fetchDogImage">Get New Dog</button>
  </div>
</template>

