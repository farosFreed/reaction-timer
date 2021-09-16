<template>
  <div class="block" @click="stopTimer" v-if="showBlock">
      click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0
      }
    },
    mounted() { //once component mounts
      setTimeout(() => {
        this.showBlock = true //show the component
        this.startTimer() //start the timer
      }, this.delay) //after this.delay amount of time
    },
    methods: {
      startTimer() {
        this.timer = setInterval(() => {this.reactionTime += 10}, 10) //add 10ms to timer every 10ms
      },
      stopTimer() {
        clearInterval(this.timer) //stop the setInterval
        this.$emit('end', this.reactionTime)//emit event for Results.vue, send reactionTime
      }
    }
}
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: green;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>