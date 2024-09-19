<script setup>
    import { ref } from 'vue'
    
    const question = ref('')
    const answer = ref(null)
    
    const getAnswer = () => {
      if (question.value.trim() === '') {
        answer.value = 'Ask'
        return
      }
      
      answer.value = Math.random() > 0.5 ? 'Yes' : 'No'
    }
    </script>
    
    <template>
  <div class="YesorNo">
    <h2>Y/N Question</h2>
    <input v-model="question" type="text" placeholder="Y/N question here" />
    <button @click="getAnswer">ASK</button>
    <p v-if="answer !== null">Answer: {{ answer }}</p>
  </div>
    </template>