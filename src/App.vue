<script setup>
import { ref } from 'vue'
import FortuneStats from './components/FortuneStats.vue';
import FortuneCustomizer from './components/FortuneCustomizer.vue';
import YesorNo from './components/YesorNo.vue';

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
  <div>
    <h2>GENIE WISH</h2>
    <img src="/darkgenie1.jpg" alt="Genie" class="genie-image">
    <p>{{ fortuneMessage }}</p>
    <button @click="generateFortune">PRESS FOR FORTUNE</button>
    <button @click="resetFortune">RESET</button>

    <YesorNo />
    <FortuneCustomizer @addFortune="addCustomFortune" />
    <FortuneStats :history="fortuneHistory" />
  </div>
</template>