<template>
  <div class="app">
    <header>
      <h1>Get random joke</h1>
    </header>
    <div class="main">
      <div class="jokegen">
        <p>{{ joke.setup }}</p>
        <h4>"{{ joke.punchline }}"</h4>
        <button @click="getJoke()" >Get Another</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";

export default {
  name: 'App',
  setup() {
    const joke = ref([])
    const options = {
      method: 'GET',
      headers: {
        'X-RapidAPI-Key': 'f6dd938eacmsh0d384b1080b54fbp10dd7cjsn5485a7bd7a65',
        'X-RapidAPI-Host': 'manatee-jokes.p.rapidapi.com'
      }
    };

    onBeforeMount(() => {
      fetch('https://manatee-jokes.p.rapidapi.com/manatees/random', options)
      .then(response => response.json())
      .then(data => {
        joke.value = data
      })
    })
    
    const getJoke = () => {
      fetch('https://manatee-jokes.p.rapidapi.com/manatees/random', options)
      .then(response => response.json())
      .then(data => {
        joke.value = data
      })
    }
    return {
      joke,
      getJoke
    }
  }
}
</script>

<style>
 * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
 }
 body {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  background-image: linear-gradient(to bottom right, #ffffff, #928aff);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 100vh;
 }
 header {
  margin-bottom: 20px;
 }
 .app {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100%;
  margin: 50% auto;
  background-image: linear-gradient(to bottom right, #928aff, #ffffff);
  padding: 20px;
  border-radius: 20px;
  margin: 0 10px;
 }
 p {
  color: #000;
  padding: auto 12px;
  font-size: 17px;
 }
 button {
  padding: 15px 20px;
  border: none;
  border-radius: 99px;
  background: #0b0470;
  color: #ffffff;
  font-size: 15px;
  font-weight: bolder;
  margin-top: 10px;
  cursor: pointer;
 }

</style>
