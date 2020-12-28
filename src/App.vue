<template>
  <div class="container">
    <div class="game" v-if="!isPlaying">
      <h1>Reaction Timer</h1>
      <button @click="start" :disabled="isPlaying">Play Game</button>
    </div>
    <Block v-if="isPlaying" :delay="delay" @endGame="endGame" />
    <Result v-if="showResult" :score="score" @closeResult="closeResult" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 5000 * Math.random() + 2000;
      this.isPlaying = true;
    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.showResult = true;
      this.score = reactionTime;
    },
    closeResult() {
      this.showResult = false;
    },
  },
};
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
.container {
  top: 0;
  width: 100%;
  height: 100%;
  display: flex;
  position: fixed;
  background: black;
  flex-direction: column;
  align-content: center;
}
.game {
  width: 300px;
  height: 200px;
  margin: auto;
}
h1 {
  color: white;
}
button {
  padding: 20px;
  color: white;
  cursor: pointer;
  border-radius: 10px;
  background: black;
  border: 1px solid white;
}
</style>
