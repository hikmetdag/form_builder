<script setup>
import DropDown from "./components/dropdown.vue"

</script>

<template>
  <main>
    <div class="left">
    <DropDown/>
    </div>

    <div class="right">right</div>
  </main>
</template>

<style scoped>
.left {
  background-color: aqua;
  width: 25%;
  max-height: 100vh;
}
.right {
  background-color: red;
  width: 75%;
  height: 100%;
}
main {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100vh;
  background-color: blueviolet;
}

@media (min-width: 400px) and (max-width: 900px) {
  main {
    flex-direction: column;
  }
}
</style>
