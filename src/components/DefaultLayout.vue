<template>
  <div class="bg-white shadow-sm h-16">
  <navbar />
<main>
  <router-view />
</main>
</div>
</template>

<script setup>
import Navbar from '../components/Navbar.vue'
</script>