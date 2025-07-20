<template>
    <div class="saved-section">
        <h2>Saved Dogs</h2>

        <div v-if="dogs.length === 0">
            <p>No Saved dogs</p>
        </div>

        <ul class="saved-list" v-else>
            <li v-for="(dog, index) in dogs" :key="index">
                <img :src="dog.url" alt="Dog" class="thumb">
                <span>{{ dog.name }}</span>
            </li>
        </ul>
    </div>
</template>

<script setup>
    defineProps({
        dogs: {
            type: Array,
            required: true
        },
    })
</script>

<style scoped>
.saved-section {
    margin-top: 40px;
}

.saved-list {
    list-style: none;
    padding: 0;
}

.saved-list li {
    display: flex;
    align-items: center;
    margin: 12px 0;
}

.thumb {
    width: 60px;
    height: 60px;
    border-radius: 8px;
    margin-right: 10px;
    object-fit: cover;
}
</style>