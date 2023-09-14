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
      <div v-if="Object.keys(dataBase).length" class="upperDiv">
        <h1>Instellingen</h1>
        <div>
          <label for="input">Vraag</label><br />
          <input type="text" v-model="dataBase[indexQuestion].query" />
        </div>

        <div v-if="dataBase[indexQuestion].text == 'Lange tekst'">
          <label for="input">Grootte tekstveld</label><br />
          <input type="range" min="1" max="50" v-model="sliderValue" />
        </div>
      </div>

      <div v-if="Object.keys(dataBase).length" class="downDiv">
        <span>PREVIEW</span> <br />
        <div></div>
        <label for="input"
          ><h2>{{ dataBase[indexQuestion]?.query }}</h2></label
        >
        <br />
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
  border-left: 1px solid rgba(24, 24, 24, 0.141);
  display: flex;
  flex-direction: column;
}
main {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100vh;
  overflow-y: hidden;
  padding-top: 1rem;
}

.upperDiv {
  max-height: 35%;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 1.3rem;
  border-bottom: 1px solid rgba(24, 24, 24, 0.141);
}
.downDiv {
  height: 65%;
  display: flex;
  flex-direction: column;
  padding: 1.3rem;
  background-color: rgba(142, 134, 134, 0.141);
}
input[type='text'] {
  width: 40%;
  height: 7vh;
  border-radius: 7px;
  padding: 5px;
}
input[type='range'] {
  width: 40%;
  cursor: pointer;
  background-color:rgba(142, 134, 134, 0.141) ;
}

textarea {
  width: 90%;
}

span {
  background-color: blue;
  color: white;
  width: 5rem;
  padding: 5px;
  border-radius: 7px;
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
