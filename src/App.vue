<script setup>
// import HomepageView from './views/HomepageView.vue'
// import FavoritePlace from './components/FavoritePlace/FavoritePlace.vue'
// import FavoritePlaces from './components/FavoritePlaces/FavoritePlaces.vue'

import LoginForm from './components/Auth/LoginForm/LoginForm.vue'
import RegistrationForm from './components/Auth/RegistrationForm/RegistrationForm.vue'
</script>

<template>
  <!-- <HomepageView /> -->
  <div class="bg-white h-screen w-[400px]">
    <!-- <FavoritePlaces /> -->
    <RegistrationForm @submit="console.log" />
    <LoginForm @submit="console.log" />
  </div>
</template>
