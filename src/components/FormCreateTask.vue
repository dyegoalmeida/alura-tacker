<template>
  <div class="box">
    <div class="columns">
        <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
          <input type="text" name="" id="" class="input" placeholder="Qual tarefa você deseja iniciar?">
        </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">
          <section>
            <strong> {{ elapsedTime }}</strong>
          </section>
          <button class="button" @click="start">
          <span class="icon">
            <i class="fas fa-play"></i>
          </span>
          <span>play</span>
          </button>
          <button class="button" @click="finish">
          <span class="icon">
            <i class="fas fa-stop"></i>
          </span>
          <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "FormCreateTask",
  data () {
    return{
      timeInSeconds: 0,
      stopwatch: 0
    }
  },
  computed: {
    elapsedTime (): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substring(11,19);
    }
  },
  methods: {
    start () {
      /**
       * 1 seg = 1000ms
       */
      this.stopwatch = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000)
    },
    finish (){
      clearInterval(this.stopwatch);
    }
  }
});
</script>

<style scoped>

</style>