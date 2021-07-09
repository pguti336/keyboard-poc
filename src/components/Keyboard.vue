<template>
  <div class="row col-7">
    <h1>Keyboard Component</h1>
    <div class="col-1" v-for="(tone, index) in tones" :key="index">
      <KeyBtn class="" :tone="tone" />
    </div>
  </div>
</template>

<script>
import KeyBtn from "./KeyBtn";
import { ref } from "vue";
export default {
  components: {
    KeyBtn,
  },
  setup() {
    const tones = ref([
      "C",
      "C#",
      "D",
      "D#",
      "E",
      "F",
      "F#",
      "G",
      "G#",
      "A",
      "A#",
      "B",
    ]);
    return { tones };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
