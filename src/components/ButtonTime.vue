<template>
  <button class="button" @click="click" :disabled="disable">
    <span class="icon">
      <i :class="icon"></i>
    </span>
    <span>{{text}}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ButtonTime",
  emits: ['clicked'],
  props: {
    disable: {
      type: Boolean
    },
    icon: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    },
  },
  methods: {
    click () : void {
      this.$emit('clicked')
    }
  }
});
</script>