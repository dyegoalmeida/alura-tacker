<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioCriacaoTarefa />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from "@/components/BarraLateral.vue";
import FormularioCriacaoTarefa from "@/components/FormularioCriacaoTarefa.vue";

export default defineComponent({
  name: 'App',
  components: {FormularioCriacaoTarefa, BarraLateral},
});
</script>

<style>
</style>
