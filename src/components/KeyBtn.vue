<template>
  <div>
    <Tone :tone="tone" v-show="showTone"></Tone>

    <button
      type="button"
      class="btn key-btn mt-5 py-3 border border-dark"
      :class="
        isSharpTone
          ? 'btn sharp-key-btn mt-5 py-3 bg-dark border border-dark'
          : 'btn key-btn mt-5 py-3 bg-white border border-dark'
      "
      @mousedown="playTone"
      @mouseleave="stop"
      @mouseup="stop"
      @touchstart="playTone"
      @touchend="stop"
      @touchcancel="stop"
    ></button>
  </div>
</template>

<script>
import {
  ref,
  computed,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
} from "vue";
import Tone from "./Tone";

export default {
  components: {
    Tone,
  },
  props: ["tone"],
  setup(props) {
    onBeforeMount(() => {
      console.log("before mount");
    });
    onMounted(() => {
      console.log("on mounted");
    });

    onBeforeUpdate(() => {
      console.log("onBeforeUpdate");
    });
    onUpdated(() => {
      console.log("onUpdated");
    });

    const isActive = ref(false);

    const playTone = () => {
      isActive.value = true;
      console.log("props.tone", props.tone);
      var audioElement = new Audio(
        `/sounds/${props.tone.replace("#", "sharp")}.mp3`
      );
      audioElement.play();
    };
    const stop = () => {
      isActive.value = false;
    };

    const showTone = computed(() => {
      return isActive.value;
    });

    const isSharpTone = computed(() => {
      if (props.tone.includes("#")) {
        return true;
      } else {
        return false;
      }
    });

    return { isActive, playTone, stop, showTone, isSharpTone };
  },
};
</script>

<style scoped>
.key-btn {
  height: 210px;
  border-radius: 0;
  color: #000;
  padding: 30px 30px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.sharp-key-btn {
  height: 105px;
  border-radius: 0;
  padding: 30px 30px;
  color: #000;
  text-align: center;
  text-decoration: none;
  font-size: 16px;
}
</style>
