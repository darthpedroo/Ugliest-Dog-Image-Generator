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
    <div class="container-fluid">
      <div class="row">
        <h1 class="text-center col-10 img-fluid mx-auto my-5 custom-font">UGLIEST DOG IMAGE GENERATOR</h1>
      </div>
      <div class="row">
        <img class="col-10 img-fluid mx-auto" :src="result"  alt="">
      </div>
 
      <div class="row">
        <button v-on:click="fetchData" type="button" class="btn btn-primary my-5 mx-auto col-10 custom-font"> OTRO PERRITO</button>
      </div>

    </div>
  
  </main>
</template>

<style scoped>
.custom-font {
    font-family: 'Rubik', sans-serif;
}

</style>
