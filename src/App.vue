<script>
  import Block from './components/Block.vue';
  import Result from './components/Result.vue';

  export default{
    name : 'App',
    components:{ Block ,Result},
    data() {
      return{
        header : "Welcome to Timer Game",
        isplayer : false,
        delay : null,
        score : null,
        showResult : false
      }     
    },
    methods:{
      start(){
        this.isplayer=true
        this.delay = 2000 + Math.random()*2000
        this.showResult = false
        // console.log(this.delay)
      },
      endGame(timeRequired){
        this.score = timeRequired
        this.isplayer = false
        this.showResult = true
      }
    }
  }

</script>

<template>
  <div class="main">
    <h1>{{ header}}</h1>
   <button @click="start" :disabled='isplayer'>play</button>

   <Block v-if='isplayer' :delay = "delay" @end="endGame"/>
   <Result v-if="showResult" :score = "score"/>
   <!-- <p v-if="showResult">{{ score }} ms</p> -->

  </div>
  
  
</template>

<style>
  .main{
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #444;
    margin-top: 60px;;
  }





</style>
