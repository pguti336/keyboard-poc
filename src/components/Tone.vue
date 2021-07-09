<template>
  <span class="tone-label">
    {{ tone }}
  </span>
</template>

<script>
import { onBeforeUnmount, onUnmounted } from "vue";
export default {
  props: ["tone"],
  setup(props) {
    onBeforeUnmount(() => {
      console.log("onBeforeUnmount tone", props.tone);
    });
    onUnmounted(() => {
      console.log("onUnmounted tone", props.tone);
    });
  },
};
</script>

<style scoped>
.tone-label {
  border-radius: 5px;
  padding: 20px;
  background-color: #fff;
  font-size: 20px;
  font-weight: 600;
}
</style>
