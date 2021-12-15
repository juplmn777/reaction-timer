<template>
  <h1>Reaction Timer</h1>

  <button @click="startGame" :disabled="isGameRunning">Play</button>
  <Results v-if="showResult" :score="score" />
  <Block v-if="isGameRunning" :delay="delay" @end="endGame" />
</template>

<script>
import Block from '@/components/Block.vue';
import Results from '@/components/Results.vue';
export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isGameRunning: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isGameRunning = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isGameRunning = false;
      this.showResult = true;
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
  color: #ff4b5c;
  margin-top: 60px;
}

button {
  padding: 10px 25px;
  border-radius: 5px;
  background: #1A1A2E;
  border: 1px solid #1A1A2E;
  color: #f1f1f1;
  box-shadow: 2px 2px 5px #000;
  text-transform: uppercase;
  font-weight: 900;
  letter-spacing: 1px;
  cursor: pointer;
}

button[disabled] {
  opacity: 0.4;
  cursor: not-allowed;
}
</style>
