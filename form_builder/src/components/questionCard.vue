<script setup>
import { defineProps } from 'vue'
defineProps({
  query: {
    type: String,
    default: ''
  },
  questionType: {
    type: String,
    default: ''
  }
})
</script>

<template>
  <div class="cardBody">
    <h2>{{ query }}</h2>
    <h4>{{ questionType }}</h4>
    <button @click="$emit('deleteQuestion')">X</button>
    <span>Vraag verwijderen</span>
  </div>
</template>
<style scoped>
.cardBody {
  position: relative;
  height: 15vh;
  background-color: rgba(142, 134, 134, 0.141);
  width: 90%;
  box-sizing: border-box;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid blue;
  border-radius: 10px;
  font-size: 1rem;
  padding-left: 1rem;
}

button {
  position: absolute;
  top: 10px;
  right: 10px;
  color: red;
  border: none;
  background-color: rgba(142, 134, 134, 0.141);
  font-size: 1.3rem;
}
button:hover {
  background-color: rgba(24, 24, 24, 0.141);
  cursor: pointer;
}
button:hover + span {
  visibility: visible;
  color:white;
  background-color: black;
  padding: 5px;
  border-radius: 7px;
}

span {
  visibility: hidden;
  position: absolute;
  top: -1.4rem;
  right: -2rem;
}
</style>
