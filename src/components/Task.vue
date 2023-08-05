<template>
  <BoxListTask>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
          <stop-watch :time-in-seconds="task.durationInSeconds" />
      </div>
    </div>
  </BoxListTask>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import StopWatch from "@/components/StopWatch.vue";
import ITask from "@/interfaces/ITask";
import BoxListTask from "@/components/BoxListTask.vue";
export default defineComponent({
  name: "Task-Task",
  components: {
    BoxListTask,
    StopWatch
  },
  props: {
    task: {
      type: Object as PropType<ITask>,
      // Ou seja não existe uma task sem essa propriedade
      required: true
    }
  }
});
</script>