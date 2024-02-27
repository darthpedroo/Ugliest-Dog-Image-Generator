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
        <h1 class="col-lg-12 col-md-10 col-sm-6 text-center mx-auto my-2 custom-font">UGLIEST DOG IMAGE GENERATOR</h1>
      </div>
      <div class="row">
        <img class="col-lg-6 col-md-8 col-sm-10 col-6 mx-auto" :src="result" alt="">
      </div>

      <div class="row">
        <button v-on:click="fetchData" type="button" class="col-lg-6 col-md-8 col-sm-10 col-6 btn btn-primary my-2 mx-auto custom-font"> OTRO PERRITO</button>
      </div>

    </div>
  
  </main>
</template>

<style scoped>
.custom-font {
    font-family: 'Rubik', sans-serif;
}

/* Small devices (≥576px) */
@media (min-width: 576px) {
  img{
    max-height:576px;
    max-width:576px;
  }
}

/* Medium devices (≥768px) */
@media (min-width: 768px) {
  img{
    max-height:768px;
    max-width:768px;
  }

}

/* Large devices (≥992px) */
@media (min-width: 992px) {
  img{
    max-height:992px;
    max-width:992px;
  }
}

/* Extra large devices (≥1200px) */
@media (min-width: 1200px) {
  img{
    max-height:992px;
    max-width:992px;
  }
  
}
</style>
