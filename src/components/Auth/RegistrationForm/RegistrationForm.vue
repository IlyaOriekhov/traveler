<script setup>
import IButton from '../../IButton/IButton.vue'
import IInput from '../../IInput/IInput.vue'
import FormContainer from '../FormContainer.vue'

import { reactive, toRaw } from 'vue'

const emit = defineEmits(['submit'])

const userData = reactive({
  name: '',
  email: '',
  password: '',
})
</script>

<template>
  <FormContainer
    @submit.prevent="emit('submit', toRaw(userData))"
    class="max-w-[500px] w-full bg-white p-10 rounded-2xl"
  >
    <IInput class="mb-4" label="Повне ім`я" placeholder="Як звати" v-model="userData.name" />
    <IInput
      class="mb-4"
      label="Електронна пошта"
      placeholder="email@gmail.com"
      v-model="userData.email"
    />
    <IInput label="Пароль" type="password" placeholder="Пароль" v-model="userData.password" />
    <IButton class="mt-10 w-full" variant="gradient" type="submit">Створити аккаунт</IButton>
  </FormContainer>
</template>
