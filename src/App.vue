<script setup>
import { useFetch } from '@vueuse/core'

const url = 'https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current=temperature_2m,weather_code&hourly=temperature_2m&daily=temperature_2m_max,temperature_2m_min&timezone=auto'


const { data, isFetching, error } = useFetch(url).json()

</script>

<template>
  <div class="p-6">
    <div v-if="error" class="text-red-500">
      Error: {{ error }}
    </div>

    <div v-else-if="isFetching">
      <p class="animate-pulse">Fetching</p>
    </div>

    <div v-else-if="data">
      <h1 class="text-2xl font-bold">{{ data.timezone }}</h1>
      <p class="text-4xl">{{ data.current.temperature_2m }}°C</p>
    </div>
  </div>
</template>

<style scoped></style>
