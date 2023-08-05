<template>
  <div class="box">
    <div class="columns">
        <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
          <input type="text" name="" id="" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="description">
        </div>
      <div class="column">
        <Timer @inTimerFinished="finishedTask"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import Timer from "@/components/Timer.vue";

export default defineComponent({
  name: "FormCreateTask",
  emits: ['onSaveTask'],
  components: {Timer},
  data () {
    return {
      description : ''
    }
  },
  methods: {
    finishedTask(elapsedTime: number) : void{
      this.$emit('onSaveTask', {
        durationInSeconds: elapsedTime,
        description: this.description
      })
    }
  }
});
</script>