<template>
  <div class="grid grid-cols-2 p-8">
    <div class="">
      <div class="bg-white shadow rounded">
        <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t">
      </div>
    </div>
    <div class="">
      <div p-3>
        <h2>{{ meal.strMeal }}</h2>
        <p>
          {{ meal.strInstructions }}
        </p>
        <a :href="meal.strYoutube" target="_blank">Video</a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axiosClient from "../axiosClient";

const route = useRoute();
const meal = ref({});

onMounted(() => {
  axiosClient.get(`lookup.php?i=${route.params.id}`)
    .then((data) => {
      meal.value = data.data.meals[0] || {}
    })
    .catch((err) => {
      console.log('error getting meal details: ', err);
    })
})
</script>