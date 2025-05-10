<script setup>
import FavoritePlace from '../FavoritePlace/FavoritePlace.vue'
import IButton from '../IButton/IButton.vue'
import { ref, reactive } from 'vue'

const buttonVariant = ref('gradient')

const changeButtonVariant = () => {
  buttonVariant.value = buttonVariant.value === 'gradient' ? 'outlined' : 'gradient'
}
</script>

<template>
  <div class="px-6">
    <div class="text-[#939393] mb-4">Додані маркери</div>

    <!-- <FavoritePlace v-for="n in 4" :key="n" /> -->
    <!-- <IButton class="w-full mt-1і">Додати маркер</IButton> -->
    <slot name="label"></slot>
    <slot name="list">
      <FavoritePlace v-for="n in 4" :key="n" />
    </slot>

    <slot></slot>
    <IButton class="w-full mt-10" :variant="buttonVariant" @click="changeButtonVariant"
      >Додати маркер</IButton
    >
  </div>
</template>
