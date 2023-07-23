<script setup>
const location = "Dhaka"
const weather = "r"
</script>

<template>
  <section class="container mx-auto flex items-center flex-col">
    <h1 class="text-center text-2xl py-10">Logic in Vue.js</h1>
    <div class="w-1/3 bg-gray-200 p-10 flex items-center flex-col space-y-10">
      <h1 class="text-3xl">{{ location }}</h1>
      <h2 class="text-2xl" v-show="weather == 's'">Weather: Sunny</h2>
      <h2 class="text-2xl" v-show="weather == 'pc'">Weather: Partly Cloudy</h2>
      <h2 class="text-2xl" v-show="weather == 'r'">Weather: Rainy</h2>
      <h2 class="text-2xl" v-show="weather == 't'">Weather: Thunderstorm</h2>
      <h2 class="text-2xl" v-show="weather == 'c'">Weather: Cyclone</h2>
      <img v-show="weather == 's'" src="https://creazilla-store.fra1.digitaloceanspaces.com/icons/7911203/weather-icon-md.png" alt="">
      <img v-show="weather == 'pc'" src="https://creazilla-store.fra1.digitaloceanspaces.com/icons/7912718/weather-icon-md.png" alt="">
      <img v-show="weather == 'r'" src="https://creazilla-store.fra1.digitaloceanspaces.com/icons/7913380/weather-icon-md.png" alt="">
      <img v-show="weather == 't'" src="https://creazilla-store.fra1.digitaloceanspaces.com/icons/7912589/weather-icon-md.png" alt="">
    </div>
  </section>
</template>

<style scoped></style>
