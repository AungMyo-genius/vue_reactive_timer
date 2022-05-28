<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me {{delay}}</div>
</template>

<script>
export default {
    props:['delay'],
    data(){
      return {
        showBlock:false,
        score:0,
        timer:null,
      }
    },
    mounted(){
      setTimeout( ()=> this.showBlock=true, this.delay);
      this.startTimer();
    },
    methods:{
      startTimer(){
        this.timer = setInterval( 
          ()=> this.score+= 1 ,1);
      },
      stopTimer(){
        clearInterval(this.timer);
         this.$emit("endGame",this.score);
      }
    }
    // updated(){
    //   console.log("data updated");
    // },
    // unmounted(){
    //   console.log("component unmounted");
    // }
}
</script>

<style>
.block{
    width:400px;
    height: 300px;
    margin: 20px auto;
    background: aquamarine;
    border-radius: 20px;
    padding-top: 30px;
}
</style>