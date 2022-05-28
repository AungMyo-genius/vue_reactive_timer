<template>
  <div>

  <h1>How Fast Can you catch me? (1ms to 2s)</h1>
  <button @click="play" :disabled="isPlaying">Play</button>

  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame"/> 
  </div>
  <div v-if="score && !isPlaying">
    <Result :score="score"></Result>
  </div>

  </div>

</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: {
    Block:Block,
    Result,
  },
  data(){
    return {
      isPlaying:false,
      delay:null,
      score:0,
    }
  },
  methods:{
    play(){
      this.isPlaying = true;
      this.delay = 200+(Math.random()*2000 + 1);
    },
    endGame(score){
      this.score=score;
      this.isPlaying=false;
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
