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
        <h1 class="col-12 text-center mx-auto my-2 custom-font">UGLIEST DOG IMAGE GENERATOR</h1>
      </div>
      <div class="row">
        <!-- Image with responsive size -->
        <img class="col-12 mx-auto my-2" :src="result" alt="" style="max-width: 100%; height: auto; width: 90%; max-width: 500px; object-fit: cover;">
      </div>

      <div class="row">
        <!-- Button with the same width as the image -->
        <button v-on:click="fetchData" type="button" class="col-12 col-md-8 btn btn-primary my-2 mx-auto custom-font" style="width: 90%; max-width: 500px;"> OTRO PERRITO</button>
      </div>
    </div>
  </main>
</template>

<style scoped>
/* Ensures that the image's width is flexible and adjusts with screen size */
img {
  max-width: 100%;
  height: auto;
  width: 90%;
  max-width: 500px;
  object-fit: cover; /* Ensures the image scales without distorting */
}

/* Optional: Custom font size for smaller screens */
@media (max-width: 768px) {
  .custom-font {
    font-size: 1.5rem;
  }
}

@media (max-width: 576px) {
  .custom-font {
    font-size: 1.25rem;
  }
}
</style>

