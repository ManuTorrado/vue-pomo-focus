<script>
import { onUpdated } from "vue";

export default {
  name: "Clock",
  props: {
    stopped: { type: Boolean, default: true },
  },
  watch: {
    stopped(val) {
      if (val) this.counting(1000);
    },
  },
  data() {
    return { Seconds: 1 };
  },
  created() {
    this.counting(1000);
  },
  methods: {
    delay(time) {
      return new Promise((resolve) => setTimeout(resolve, time));
    },
    counting(n) {
      console.log(n / 1000 + " segundos pasaron");
      this.delay(n).then(() => {
        if (this.stopped) {
          console.log(this.Seconds);
          this.counting(1000);
          this.Seconds++;
        }
      });
    },
  },
};

onUpdated(() => {
  console.log("updated");
  this.stopped = !this.stopped;
});
</script>

<template>
  <div>
    <h2>{{ stopped }}</h2>
    <h3>{{ Seconds }}</h3>
  </div>
</template>
