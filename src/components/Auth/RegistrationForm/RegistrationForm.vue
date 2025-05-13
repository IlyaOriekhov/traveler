<script setup>
import IButton from '../../IButton/IButton.vue'
import IInput from '../../IInput/IInput.vue'

import { reactive, toRaw } from 'vue'

const props = defineProps({
  isLoading: {
    default: false,
    type: Boolean,
  },
})

const emit = defineEmits(['submit'])

const userData = reactive({
  name: '',
  email: '',
  password: '',
})
</script>

<template>
  <form @submit.prevent="emit('submit', toRaw(userData))">
    <IInput class="mb-4" label="Повне ім`я" placeholder="Як звати" v-model="userData.name" />
    <IInput
      class="mb-4"
      label="Електронна пошта"
      placeholder="email@gmail.com"
      v-model="userData.email"
    />
    <IInput label="Пароль" type="password" placeholder="Пароль" v-model="userData.password" />
    <IButton class="mt-10 w-full" variant="gradient" type="submit" :is-loading="props.isLoading">
      Створити аккаунт
    </IButton>
  </form>
</template>
