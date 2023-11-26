<template>
  <div class="flex flex-col p-8 justify-center items-center">
    <div class="flex gap-3 mt-2">
      <router-link :to="{ name: 'byLetter', params: {letter}}" v-for="letter in letters" :key="letter"> {{  letter }}</router-link>
    </div>
  </div>
  
  <pre>{{ ingredients }}</pre>
</template>

<script setup>
import { onMounted, ref } from "vue";
import axiosClient from "../axiosClient.js"
import MealsByName from "../views/MealsByName.vue"


const ingredients = ref([]);
onMounted(async () => {
  const response = await axiosClient.get('list.php?i=list');
  ingredients.value = response.data;
})

</script>