<template>
  <h1>Reaction Timer</h1>
  <button :disabled="isPlaying" @click="start">Start</button>
  <button :disabled="!isPlaying" @click="stop">Stop</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <!-- <p v-if="score">Score: {{ score }} ms</p> -->
  <Results v-if="score" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000;
      this.isPlaying = true;
      this.score = null;
    },
    stop() {
      this.isPlaying = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  margin-left: 10px;
  color: white;
  background: #0faf87;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
