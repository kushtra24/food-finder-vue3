<template>
  <div class="flex flex-col p-8 justify-center items-center">
    <div class="flex gap-3 mt-2">
      <router-link :to="{ name: 'byLetter', params: {letter}}" v-for="letter in letters" :key="letter"> {{  letter }}</router-link>
    </div>
  </div>
</template>

<script setup>

const letters = "abcdefghijklmnopqrstuvwxyz".split("");
</script>