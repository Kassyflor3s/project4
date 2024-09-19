<script setup>
import { ref } from 'vue'

const tips = ref([
  "Try again tomorrow",
  "Take a break.",
  "Take a nap.",
  "Don't be afraid.",
])
</script>

<template>
  <div class="quicktips">
    <h3>↓Advice Below↓</h3>
      <li v-for="tip in tips" :key="tip">{{ tip }}</li>
  </div>
</template>