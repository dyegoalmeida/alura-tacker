<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <StopWatch :time-in-seconds="timeInSeconds"/>
<!--    <button class="button" @click="start" :disabled="stopwatchStart">-->
<!--          <span class="icon">-->
<!--            <i class="fas fa-play"></i>-->
<!--          </span>-->
<!--      <span>play</span>-->
<!--    </button>-->
<!--    <button class="button" @click="finish" :disabled="!stopwatchStart">-->
<!--          <span class="icon">-->
<!--            <i class="fas fa-stop"></i>-->
<!--          </span>-->
<!--      <span>stop</span>-->
<!--    </button>-->
    <ButtonTime @clicked="start" icon="fas fa-play" text="play" :disable="stopwatchStart" />
    <ButtonTime @clicked="finish" icon="fas fa-stop" text="stop" :disable="!stopwatchStart" />
  </div>
</template>
<script lang="ts">
import {defineComponent} from "vue";
import StopWatch from "@/components/StopWatch.vue"
import ButtonTime from "@/components/ButtonTime.vue";

export default defineComponent({
  name: 'TimerTimer',
  emits: [
      'inTimerFinished'
  ],
  components: {ButtonTime, StopWatch},
  data () {
    return{
      timeInSeconds: 0,
      stopwatch: 0,
      stopwatchStart: false,
    }
  },
  methods: {
    start () {
      /**
       * 1 seg = 1000ms
       */
      this.stopwatchStart = true;
      this.stopwatch = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000)
    },
    finish (){
      this.stopwatchStart = false;
      clearInterval(this.stopwatch);
      this.$emit('inTimerFinished', this.timeInSeconds);
      this.timeInSeconds = 0
    }
  }
})
</script>