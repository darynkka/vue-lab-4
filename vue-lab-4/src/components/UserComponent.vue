<template>
  <div class="user-card" :class="{ adult: userData.age > 18, minor: userData.age <= 18 }">
    <img :src="`/src/img/${userData.photo}`" alt="User photo" class="user-photo" />
    <p class="user-name">{{ userData.firstName }} {{ userData.lastName }}</p>
    <p class="user-gender">Gender: {{ userData.gender }}</p>
    <p v-if="userData.age > 18" class="user-age">Age: {{ userData.age }}</p>
    <p class="user-position">Position: {{ userData.position }}</p>
    <ul class="user-hobbies">
      <li v-for="(hobby, index) in userData.hobbies" :key="index">{{ hobby }}</li>
    </ul>
  </div>
</template>

<script setup lang="ts">
interface User {
  firstName: string
  lastName: string
  gender: string
  age: number
  position: string
  photo: string
  hobbies: string[]
}

const props = defineProps<{ userData: User }>()
</script>

<style scoped>
.user-card {
  border: 1px solid #ccc;
  padding: 16px;
  border-radius: 8px;
  margin-bottom: 12px;
  text-align: center;
  transition: background-color 0.3s ease;
}

.adult {
  background-color: #e0f7fa;
}

.minor {
  background-color: #ffe0b2;
}

.user-photo {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 12px;
}

.user-name {
  font-size: 1.2em;
  font-weight: bold;
}

.user-gender,
.user-age,
.user-position {
  margin: 4px 0;
}

.user-hobbies {
  list-style-type: none;
  padding: 0;
}

.user-hobbies li {
  margin: 2px 0;
}
</style>
