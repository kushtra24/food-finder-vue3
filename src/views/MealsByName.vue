<template>
  <div class="flex flex-col p-8 justify-center items-center">
    <input name="meals" type="text" class="w-full rounded border-2 border-grey-100" placeholder="Search" @change="searchMeals" v-model="keyword">
  </div>
  <div class="grid grid-cols-1 md:grid-cols-5 gap-5 p-8">
    <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded">
      <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t">
      <h3 ml-6 font-semibold><router-link :to="{name: 'mealDetails',params: {id: meal.idMeal}}">{{ meal.strMeal }}</router-link></h3>
      <div p-3>
        <a :href="meal.strYoutube" target="_blank">Video</a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import store from '../store'
import { useRoute } from "vue-router"

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch('searchMeals', keyword.value);
}

onMounted(() => {
  keyword.value = route.params.name;
  if(keyword.value) {
    searchMeals();
  }
})

</script>