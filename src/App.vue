<template>
    <main>
        <small>ADVICE #{{quote_index}} </small>
        <p>{{quote}}</p>
        <Divider/>
        <Dice @click="change_quote"/>
    </main>
</template>

<script setup>
import data from '../data/quotes.json'
import Dice from './components/dice_svg.vue'
import Divider from './components/divider_svg.vue'
import { ref, onBeforeMount } from 'vue';

const quote = ref('')
const quote_index = ref(0)

onBeforeMount( () => {
  quote_index.value = Math.floor(Math.random() * data.length)
  quote.value = data[quote_index.value].quote
})

const change_quote = () => {
  quote_index.value = Math.floor(Math.random() * data.length)
  quote.value = data[quote_index.value].quote
}

</script>

<style>
body {
  font-family: 'Manrope', sans-serif;
  background: hsl(218, 23%, 16%);
  padding: 0;
  box-sizing: border-box;
  margin: auto;
  height: 100vh;
  display: grid;
  place-content: center;
}

main {
  background: hsl(217, 19%, 24%);
  color: hsl(193, 38%, 86%);
  width: 200px;
  min-width: fit-content;
  min-height: fit-content;
  border-radius: 10px;
  padding: 25px;
  text-align: center;
  position: relative;
  display: grid;
  padding-bottom: 50px;
  line-height: 24px;
}

small {
  color: hsl(150, 100%, 66%);
  font-weight: 700;
  font-size: 11px;
}

</style>