<!-- App.vue -->

<template>
  <div>
    <div id="navbar" class="container">
      <div id="title">Polls attempt of a website</div>
      <div id="logo">
        <img src="./assets/cow.jpg" alt="macad cow" />
      </div>
    </div>

    <div id="flex">
      <div id="sidebar" class="container">
        <input v-model="inputText" class="definition-input" />
        <button @click="doSomething">Submit</button>
        <button @click="refresh">Reset</button>
        
        <button @click="updateText">Recite me a poem</button>
      </div>
      <div id="main" class="container">
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

// Array of coding poems with titles
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
    text: inputText.value,
  };
  paragraphs.value.push(newParagraph);
  inputText.value = "";
}

function refresh() {
  paragraphs.value = [];
}

function updateText() {
  // Randomly select a coding poem
  const randomPoemIndex = Math.floor(Math.random() * codingPoems.length);
  text.value = `${codingPoems[randomPoemIndex].title}: ${codingPoems[randomPoemIndex].text}`;
}
</script>

<style src="./styles/website-styles.css" />
