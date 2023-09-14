<script setup>
import DropDown from './components/dropdown.vue'
import { ref } from 'vue'
const dataBase = ref('')
//Default value of textarea
const sliderValue = ref(15)
//Get index of question from child component
const indexQuestion = ref(0)
const getIndex = (index) => {
  indexQuestion.value = index
}
//Getting questions from child component
const getQuestions = (questions) => {
  dataBase.value = questions
}
</script>

<template>
  <main>
    <div class="left">
      <DropDown @question="getQuestions" @getIndex="getIndex" />
    </div>

    <div class="right">
      <div v-if="Object.keys(dataBase).length">
        <h1>Instellingen</h1>
        <label for="vraag">Vraag</label><br />
        <input type="text" v-model="dataBase[indexQuestion].query" />
        <div v-if="dataBase[indexQuestion].text == 'Lange tekst'">
          <input type="range" min="1" max="50" v-model="sliderValue" />
        </div>
      </div>

      <div v-if="Object.keys(dataBase).length">
        <span>PREVIEW</span> <br />
        <label for="input">{{ dataBase[indexQuestion]?.query }}</label> <br />
        <textarea
          v-if="dataBase[indexQuestion].text == 'Lange tekst'"
          :style="{ height: `${sliderValue}vh` }"
        />
        <input v-else type="text" />
      </div>
    </div>
  </main>
</template>

<style scoped>
* {
  box-sizing: border-box;
  padding: 0%;
  margin: 0%;
}
body {
  margin: 0%;
}
.left {
  width: 25%;
  max-height: 100vh;
  margin: 0%;
}
.right {
  width: 75%;
  max-height: 100vh;
  border-left: 1px solid red;
}
main {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100vh;
  overflow-y: hidden;
}

@media (max-width: 990px) {
  main {
    flex-direction: column;
  }
  .left {
    width: 100%;
  }
  .right {
    width: 100%;
  }
}
</style>
