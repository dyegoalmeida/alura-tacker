<template>
  <header>
      <h1>
          <img src="../assets/logo.png" alt="">
      </h1>
    <button class="button" @click="whenChangeTheme">
      {{ textButtonTheme }}
    </button>
  </header>

</template>

<script lang="ts">
import {defineComponent} from "vue";

export default defineComponent({
  name: "SideBar",
  emits: ['whenChangeTheme'],
  data () {
    return {
      modeDarkModeActive: false
    }
  },
  computed: {
    textButtonTheme () {
      if (this.modeDarkModeActive) {
        return 'Desativar modo escuro';
      }
      return 'Ativar modo escuro';
    }
  },
  methods: {
    whenChangeTheme () {
      this.modeDarkModeActive = !this.modeDarkModeActive;
      this.$emit('whenChangeTheme', this.modeDarkModeActive);
    }
  }
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>