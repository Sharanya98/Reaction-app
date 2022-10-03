<template>
  <div class="block" v-if="showTimer" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data(){
    return{
        showTimer : false,
        timer : null,
        timeTaken : 0
    }
    
  },
  methods: {
    startTimer(){
        this.timer = setInterval(()=>{
             this.timeTaken += 10
        },10)
       
    },
    stopTimer(){
        clearInterval(this.timer)
        // console.log(this.timeTaken)
        this.$emit("end",this.timeTaken)

    }
  },
  mounted() {
    console.log("mounted");
    setTimeout(() =>{
        this.showTimer = true
        console.log(this.delay)
        this.startTimer()
    },this.delay)
  },
  unmounted(){
    console.log("unmounted")
  },
  updated(){
    console.log("updated")
  }
    
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>