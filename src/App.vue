<template>
<h1> Kawla's Reaction Timer</h1>
<button @click="start" :disabled="buttonDisabled" >play </button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<p v-if="showResults"> Reaction time: {{ score  }} ms</p>

</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results, 
  },
  data () {
    return {
      isPlaying: false, 
      delay: null, 
      score: null, 
      showResults: false,
      buttonDisabled: false
    }

  },
  methods: {
    start() {
      // here we've set the delay to be between 2000 - 5000 ms. Math.random() is a number between 0-1
      this.delay = 2000 + Math.random() * 5000 
      this.isPlaying = true
      this.showResults = false 
      this.buttonDisabled = true

    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
      this.buttonDisabled = false

    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
