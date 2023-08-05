<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <FormCreateTask @onSaveTask="saveTask" />
      <div class="list">
        <TaskTask v-for="(task, index) in tasks" :key="index" :task="task"/>
        <BoxListTask v-if="emptyList">
          Você não está muito produtivo hoje
        </BoxListTask>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import {defineComponent} from 'vue';
import SideBar from "@/components/SideBar.vue";
import FormCreateTask from "@/components/FormCreateTask.vue";
import TaskTask from "@/components/Task.vue";
import ITask from "@/interfaces/ITask";
import BoxListTask from "@/components/BoxListTask.vue";

export default defineComponent({
  name: 'App',
  components: {BoxListTask, TaskTask, FormCreateTask, SideBar},
  data () {
    return {
      tasks: [] as ITask[]
    }
  },
  computed: {
    emptyList () : boolean {
      return this.tasks.length === 0;
    }
  },
  methods: {
    saveTask(task: ITask){
      this.tasks.push(task)
    }
  }
});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
