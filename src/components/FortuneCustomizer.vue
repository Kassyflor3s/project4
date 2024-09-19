<script setup>
import { ref } from 'vue'

const newFortune = ref("")
const emit = defineEmits(['addFortune'])

const addCustomFortune = () => {
  if (newFortune.value.trim() !== "") {
    emit('addFortune', newFortune.value)
    newFortune.value = ""
  }
}
</script>

<template>
  <div>
    <h3>Add Your Fortune</h3>
    <input type="text" id="NewFortune" v-model="newFortune" placeholder="Custom fortune" />
    <button @click="addCustomFortune">Add</button>
  </div>
</template>