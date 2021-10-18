<template>
<main class="fluid-container bg-dark">
<div class="container text-light">
  <h1 class="text-center pt-5">Astronomy Picture Of the Day</h1>
  <h3 class="text-center pb-5" v-text="date"></h3>
  <img :src="imgOfTheDay" alt="Image of the day" class="rounded img-fluid mx-auto d-block">
  <p class="text-justify pt-5 mx-4" v-text="explanation"></p>
</div>

<footer class="text-light text-center p-5">
  <p>
    Powered by 
    <a class="text-light" href="https://daviiduhh.com">daviiduhh.com</a>
  </p>
</footer>
</main>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      date: null,
      explanation: null,
      imgOfTheDay: null
    }
  },
  async mounted() {
    const res = await fetch('https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY');
    const data = await res.json();

    this.date = data.date;
    this.explanation = data.explanation;
    this.imgOfTheDay = data.hdurl;
  }
}
</script>

<style>
  a {
    text-decoration: none;
    font-weight: 600;
  }
</style>
