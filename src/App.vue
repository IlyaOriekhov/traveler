<script setup>
// import HomepageView from './views/HomepageView.vue'
// import FavoritePlace from './components/FavoritePlace/FavoritePlace.vue'
import FavoritePlaces from './components/FavoritePlaces/FavoritePlaces.vue'
import { MapboxMap, MapboxMarker } from '@studiometa/vue-mapbox-gl'

import MarkerIcon from './components/icons/MarkerIcon.vue'

import 'mapbox-gl/dist/mapbox-gl.css'
import { ref } from 'vue'

import { mapSettings } from './map/settings'

// import LoginForm from './components/Auth/LoginForm/LoginForm.vue'
// import RegistrationForm from './components/Auth/RegistrationForm/RegistrationForm.vue'
// import CreateNewPlaceModal from './components/CreateNewPlaceModal/CreateNewPlaceModal.vue'

// const isOpen = ref(true)
// const closeModal = () => {
//   isOpen.value = false
// }
// const openModal = () => {
//   isOpen.value = true
// }

const favoritePlaces = [
  {
    id: 1,
    title: 'New place 1',
    description: 'SUper description 1',
    img: '',
    lngLat: [30.523333, 50.490001],
  },
  {
    id: 2,
    title: 'New place 2',
    description: 'SUper description 2',
    img: '',
    lngLat: [30.523333, 50.450001],
  },
]

const activeId = ref(null)
const map = ref(null)

const changeActiveId = (id) => {
  activeId.value = id
}

const changePlace = (id) => {
  const { lngLat } = favoritePlaces.find((place) => place.id === id)
  changeActiveId(id)
  map.value.flyTo({ center: lngLat })
}
</script>

<template>
  <!-- <HomepageView /> -->
  <div class="bg-white h-screen w-[400px]">
    <FavoritePlaces :items="favoritePlaces" :active-id="activeId" @place-clicked="changePlace" />

    <div class="w-full h-full flex items-center justify-center text-6xl">
      <MapboxMap
        class="w-full h-full"
        :center="[30.523333, 50.450001]"
        :zoom="10"
        :access-token="mapSettings.apiToken"
        :map-style="mapSettings.style"
        @mb-created="(mapInstance) => (map = mapInstance)"
      >
        <MapboxMarker v-for="place in favoritePlaces" :key="place.id" :lngLat="place.lngLat">
          <button @click="changeActiveId(place.id)">
            <MarkerIcon class="h-8 w-8" />
          </button>
        </MapboxMarker>
      </MapboxMap>
    </div>
    <button @click="openModal">Click me</button>

    <RegistrationForm @submit="console.log" />
    <LoginForm @submit="console.log" />

    <!-- <IModal /> -->
    <CreateNewPlaceModal :is-open="isOpen" @close="closeModal" />
  </div>
</template>
