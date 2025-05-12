<script setup>
// import HomepageView from './views/HomepageView.vue'
// import FavoritePlace from './components/FavoritePlace/FavoritePlace.vue'
// import FavoritePlaces from './components/FavoritePlaces/FavoritePlaces.vue'
import { ref } from 'vue'

import LoginForm from './components/Auth/LoginForm/LoginForm.vue'
import RegistrationForm from './components/Auth/RegistrationForm/RegistrationForm.vue'
import CreateNewPlaceModal from './components/CreateNewPlaceModal/CreateNewPlaceModal.vue'

const isOpen = ref(true)
const closeModal = () => {
  isOpen.value = false
}
const openModal = () => {
  isOpen.value = true
}
</script>

<template>
  <!-- <HomepageView /> -->
  <div class="bg-white h-screen w-[400px]">
    <!-- <FavoritePlaces /> -->
    <button @click="openModal">Click me</button>

    <RegistrationForm @submit="console.log" />
    <LoginForm @submit="console.log" />

    <!-- <IModal /> -->
    <CreateNewPlaceModal :is-open="isOpen" @close="closeModal" />
  </div>
</template>
