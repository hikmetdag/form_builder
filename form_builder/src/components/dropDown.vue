<script setup>
import { ref } from 'vue'
const selected = ref('')
const showDropDown = ref(false)
</script>
<template>
  <div class="dropdown">
    <button @click="showDropDown = !showDropDown">Vraag toevoegen &#x25be;</button>
    <select v-if="showDropDown" v-model="selected" multiple>
      <option value="Lang">Lange tekst</option>
      <option value="Kort">Korte tekst</option>
    </select>
  </div>
</template>

<style scoped>
.dropdown {
  display: flex;
  flex-direction: column;
}
select {
  width: 30%;
  height: 10vh;
  padding: 5px;
}
option{
  padding: 4px;
}</style>