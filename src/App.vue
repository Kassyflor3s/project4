<script setup>
import FortuneCustomizer from './components/FortuneCustomizer.vue';
import YesorNo from './components/YesorNo.vue';
import FortuneAdvice from './components/FortuneAdvice.vue';

import { ref } from 'vue'

const fortunes = ref([
  "Luck is the residue of design.",
  "Skill comes from diligence.",
  "Pleasures await you by the sea.",
  "Ignore previous fortunes.",
  "You create your own stage and your audience is waiting.",
  "Laugh long, loud, and often.",
  "The stat of riches is shining on you.",
  "If you don't like the fortune, don't eat the cookie.",
  "You will be hungry again in 10 minutes.",
  "Love will come soon."
])

const fortuneHistory = ref([])

const fortuneMessage = ref("A click away from your fortune.")

const generateFortune = () => {
  const randomIndex = Math.floor(Math.random() * fortunes.value.length)
  fortuneMessage.value = fortunes.value[randomIndex]
  fortuneHistory.value.push(fortuneMessage.value)
}

const resetFortune = () => {
  fortuneMessage.value = "Your fortune awaits..."
}

const addCustomFortune = (newFortune) => {
  fortunes.value.push(newFortune)
}
</script>

<template>
  <div class="container">
    <h2>GENIE WISH</h2>
    <img src="/darkgenie1.jpg" alt="Genie" class="genie-image">

    <div class="fortune-section">
      <p id="fortune">{{ fortuneMessage }}</p>
      <button @click="generateFortune">PRESS FOR FORTUNE</button>
      <button @click="resetFortune">RESET</button>
    </div>

    <FortuneCustomizer @addFortune="addCustomFortune" />
    <h2>___________________________</h2>
    <YesorNo />
    <h3>___________________________</h3>
    <FortuneAdvice />
  </div>
</template>
