<script>
import { ref } from "vue";
import Clock from "./Clock.vue";

export default {
  data() {
    return {
      stopped: true,
    };
  },
  components: { Clock },

  methods: {
    setClock() {
      this.stopped = !this.stopped;
    },
  },
};

const setClock = () => {
  console.log("STOPPED");
};
</script>

<template>
  <div>
    <h1>Vue Pomo Focus</h1>
    <Clock v-bind:stopped="stopped" />
    <button @click="setClock">Stop</button>
  </div>
</template>
