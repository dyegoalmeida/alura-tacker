<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <FormCreateTask />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from "@/components/SideBar.vue";
import FormCreateTask from "@/components/FormCreateTask.vue";

export default defineComponent({
  name: 'App',
  components: {FormCreateTask, SideBar},
});
</script>

<style>
</style>
