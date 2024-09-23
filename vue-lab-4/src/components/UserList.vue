<template>
  <div class="user-list">
    <div class="toolbar">
      <button @click="filterGender('Чоловічий')">Чоловічий</button>
      <button @click="filterGender('Жіноча')">Жіноча</button>
      <button @click="filterGender('Усі')">Усі</button>
    </div>
    <div v-if="filteredUsers.length === 0">Список юзерів пустий</div>
    <div v-else class="user-cards">
      <UserComponent v-for="(user, index) in filteredUsers" :key="index" :userData="user" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import UserComponent from './UserComponent.vue'

interface User {
  firstName: string
  lastName: string
  gender: string
  age: number
  position: string
  photo: string
  hobbies: string[]
}

const users = ref<User[]>([
  {
    firstName: 'Василь',
    lastName: 'Чепурний',
    gender: 'Чоловічий',
    age: 25,
    position: 'Механік',
    photo: 'photo9.jpg',
    hobbies: ['Читання', 'Пиво']
  },
  {
    firstName: 'Леся',
    lastName: 'Чепурна',
    gender: 'Жіноча',
    age: 30,
    position: 'Домогосподарка',
    photo: 'photo10.jpg',
    hobbies: ['Малювання', 'Дизайн']
  },
  {
    firstName: 'Петро',
    lastName: 'Наливайко',
    gender: 'Чоловічий',
    age: 17,
    position: 'Student',
    photo: 'photo1.jpg',
    hobbies: ['Промахувати пари']
  },
  {
    firstName: 'Стасік',
    lastName: 'Кавуни',
    gender: 'Чоловічий',
    age: 20,
    position: 'Продавець',
    photo: 'photo3.jpg',
    hobbies: ['Спорт', 'Відеоігри']
  },
  {
    firstName: 'Галя',
    lastName: 'Город',
    gender: 'Жіноча',
    age: 22,
    position: 'Продає кабачки',
    photo: 'photo6.jpg',
    hobbies: ['Кулінарія']
  },
  {
    firstName: 'Олександр',
    lastName: 'Бім',
    gender: 'Чоловічий',
    age: 35,
    position: 'Програміст',
    photo: 'photo4.jpg',
    hobbies: ['Читання', 'Подорожі']
  },
  {
    firstName: 'Владислав',
    lastName: 'Офіснік',
    gender: 'Чоловічий',
    age: 28,
    position: 'Бізнесмен',
    photo: 'photo5.jpg',
    hobbies: ['Красти гроші']
  },
  {
    firstName: 'Ліля',
    lastName: 'М',
    gender: 'Жіноча',
    age: 40,
    position: 'Безробітня',
    photo: 'photo2.jpg',
    hobbies: ['Музика']
  },
  {
    firstName: 'Ванька',
    lastName: 'Встанька',
    gender: 'Чоловічий',
    age: 19,
    position: 'Алкаш',
    photo: 'photo7.jpg',
    hobbies: ['Фільми']
  },
  {
    firstName: 'Альона',
    lastName: 'Модна',
    gender: 'Жіноча',
    age: 29,
    position: 'Журналіст',
    photo: 'photo8.jpg',
    hobbies: ['Поезія']
  }
])

const filteredUsers = ref<User[]>([...users.value])

const filterGender = (gender: string) => {
  if (gender === 'Усі') {
    filteredUsers.value = users.value
  } else {
    filteredUsers.value = users.value.filter((user) => user.gender === gender)
  }
}
</script>

<style scoped>
.user-cards {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}
.user-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  max-width: 1200px;
  margin: 0 auto;
}

.user-card {
  width: 300px;
  margin: 12px;
  border: 1px solid #ccc;
  padding: 16px;
  border-radius: 8px;
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

.toolbar {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.toolbar button {
  margin: 0 10px;
  padding: 8px 16px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.toolbar button:hover {
  background-color: #45a049;
}
</style>
