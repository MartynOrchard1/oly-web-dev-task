<template>
    <div class="saved-seciton">
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