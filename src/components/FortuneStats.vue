<script setup>
import { computed } from 'vue'

const props = defineProps({
  history: {
    type: Array,
    require: true
  }
})

const totalFortunes = computed(() => props.history.length)

const mostFrequentFortune = computed(() => {
  if (props.history.length === 0) return "Empty."

  const frequencyMap = props.history.reduce((acc, fortune) => {
    acc[fortune] = (acc[fortune] || 0) + 1
    return acc
  }, {})

  return Object.keys(frequencyMap).reduce((a, b) => frequencyMap[a] > frequencyMap[b] ? a : b)
})
</script>

<template>
  <div>
    <h3>Most Frequent:</h3>
    <p id="most-frequent">{{ mostFrequentFortune }}</p>
  </div>
</template>