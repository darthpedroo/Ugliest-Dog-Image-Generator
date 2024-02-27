<script setup>
import { ref } from 'vue'
const result = ref(null)

// Define a function to fetch data
async function fetchData() {
  try {
    const response = await fetch('https://dog.ceo/api/breeds/image/random')
    const data = await response.json()
    console.log("DATA", data)
    result.value = data.message
    
  } catch (error) {
    console.error('Error fetching data:', error)
  }
}

// Call the fetchData function when the component is mounted
fetchData()

// Expose the reactive result object
defineExpose({ result })
</script>

<template>

  <main>
    <h1>UGLIEST DOG IMAGE GENERATOR</h1>
    <img :src="result"  alt="" width="300px" height="300px">
    <button v-on:click="fetchData"> Otro Perrito</button>
    
  </main>
</template>

<style scoped>


</style>
