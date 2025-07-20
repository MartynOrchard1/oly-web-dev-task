<template>
    <div class="form-container">
        <h2>Create a Dog</h2>
        <form @submit.prevent="handleSubmit">
            <label for="name">Dog Name</label>
            <input type="text" id="name" v-model="dogName" required />
        </form>
    </div>
</template>