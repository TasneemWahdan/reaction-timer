<template>
 <h1>Ninja Reaction Timer</h1>
 <button @click="start" :disabled="isPlaying">play</button>
 <BlockToBeClicked v-if="isPlaying" :delay="delay" @endGame="endGame"/>
 
 <ClickTimerResult v-if="showResults" :score="score" />

 
</template>

<script>
import BlockToBeClicked from './components/BlockToBeClicked.vue'
import ClickTimerResult from './components/ClickTimerResult.vue';


export default {
  name: 'App',
  components: { BlockToBeClicked, ClickTimerResult },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showResults: false,
    }
  },
  methods:{
    start(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 1000 // between 2 and 7 seconds
      this.showResults = false
      //console.log(this.delay)
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.showResults = true
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
  button {
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
