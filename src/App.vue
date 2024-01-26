<!-- App.vue -->

<template>
  <div>
    <div id="navbar" class="container">
      <div id="title">Poll's poetic website</div>
      <div id="logo">
        <img src="./assets/cow.jpg" alt="macad cow" />
      </div>
    </div>

    <div id="flex">
      <div id="sidebar" class="container">
        <!-- Existing input and buttons -->

        <!-- <input v-model="inputText" class="definition-input" />
        <button @click="doSomething">Submit</button>
        <button @click="refresh">Reset</button> -->

        <button @click="updateText">Recite me a poem</button>
          <br>
        <!-- New input fields and buttons -->
        <input v-model="selector" placeholder="CSS Selector" />
        <br>
        <input v-model="color" placeholder="Color" />
          <br>
        <button @click="changeColor">Change Color</button>
        <button @click="changeColor, updateText"> change both </button>
      </div>

      <div id="main" class="container" :style="{ backgroundColor: mainBackgroundColor }">
        <p>{{ text }}</p>
        <p v-for="paragraph in paragraphs" :key="paragraph.id">{{ paragraph.text }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const inputText = ref("");
const paragraphs = ref([]);
const text = ref("Initial text");
const selector = ref("");
const color = ref("");
const mainBackgroundColor = ref("");

const codingPoems = [
  { title: "The Coder's Dream", text: "Roses are red, violets are blue, unexpected '}' on line 32." },
  { title: "Code Poet", text: "I'm not a coder, I'm a code poet." },
  { title: "Debugging Blues", text: "Debugging is like being the detective in a crime movie where you are also the murderer." },
  { title: "The Code Symphony", text: "In the silence of the night, the code symphony plays its melody." },
  { title: "Ode to the Compiler", text: "Oh, compiler, with your discerning eye, turn my code errors into butterflies." },
];

function doSomething() {
  const newParagraph = {
    id: Date.now(),
    text: inputText,
  };
  paragraphs.push(newParagraph);
  inputText.value = "";
}

function refresh() {
  paragraphs.value = [];
}

function updateText() {
  const randomPoemIndex = Math.floor(Math.random() * codingPoems.length);
  text.value = `${codingPoems[randomPoemIndex].title}: ${codingPoems[randomPoemIndex].text}`;
}

function changeColor() {
  mainBackgroundColor.value = color.value;
}
</script>

<style>
/* styles/website-styles.css */

html {
  background-color: rgb(255, 247, 247);
  color: rgb(255, 255, 255);
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

img {
  height: 100%;
  width: auto;
}

#navbar {
  height: 50px;
  border-color: red;
}

#flex {
  display: flex;
  height: calc(100vh - 50px);
}

#sidebar {
  width: 30%;
  border-color: blue;
}

#main {
  width: 70%;
  border-color: rgb(255, 255, 255);
  font-size: 20px;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

#title {
  width: 70%;
  float: left;
  font-size: 30px;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

#logo {
  width: 30%;
  height: 100%;
  float: right;
  text-align: right;
}

.container {
  border-style: dotted;
  border-width: 1px;
}

.dynamic-color {
  color: inherit; /* or specify the default color if needed */
}


/* button styles */

button {
    background-color: #b719b7;
    border: #6fb8ff;
    color: black;
    padding: 10px 15px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 18px;
    transition: all 0.3s ease-in-out;
  }
  
  button:hover {
    background-color: #1E90FF;
    box-shadow: 3px 3px black;
  }



</style>
