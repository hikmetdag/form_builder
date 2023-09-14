<script setup>
import { ref, watchEffect } from 'vue'
import questionCard from './questionCard.vue'
//This is selection of dropdown option
const selected = ref(null)
//Visibility of dropdown
const showDropDown = ref(false)
//Created questions
const questions = ref([])

//Sending data of 'questions' to parent component
const emit = defineEmits(['question'])
watchEffect(() => {
  emit('question', questions.value)
})

//Removing questions card
const removeQuestion = (index) => {
  questions.value.splice(index, 1)
}

//Saving questions.
const addQuestion = () => {
  if (selected.value == 'Lang') {
    questions.value.push({ query: 'Wat zijn je woonwensen?', text: 'Lange tekst' })
  } else {
    questions.value.push({ query: 'Wat is je naam?', text: 'Korte tekst' })
  }
  showDropDown.value = false
}

</script>
<template>
  <div class="dropdown">
    <ul v-for="(question, index) in questions" :key="index">
      <li @click="$emit('getIndex', index)">
        <questionCard
          @deleteQuestion="removeQuestion(index)"
          :query="question.query"
          :questionType="question.text"
        />
      </li>
    </ul>
    <button @click="showDropDown = !showDropDown">Vraag toevoegen &#x25be;</button>
    <select v-if="showDropDown" v-model="selected" multiple>
      <option @click="addQuestion" value="Lang">Lange tekst</option>
      <option @click="addQuestion" value="Kort">Korte tekst</option>
    </select>
  </div>
</template>

<style scoped>
button {
  height: 2rem;
  width: 90%;
  align-self: center;
  border-radius: 5px;
}
button:hover {
  background-color: rgba(24, 24, 24, 0.141);
  cursor: pointer;
}
li {
  list-style-type: none;
}
ul {
  padding-left: 0;
}
.dropdown {
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
}
select {
  width: 30%;
  height: 10vh;
  padding: 5px;
  margin-left: 1rem;
  border-radius: 8px;
}
option {
  padding: 4px;
  background-color: white;
}
option:hover {
  background-color: rgba(24, 24, 24, 0.141);
  cursor: pointer;
}
</style>
