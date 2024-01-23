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

        <!-- New input fields and buttons -->
        <input v-model="selector" placeholder="CSS Selector" />
        <input v-model="color" placeholder="Color" />
        <button @click="changeColor">Change Color</button>
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

<style src="./styles/website-styles.css" />
