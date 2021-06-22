<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div>
    {{ count }}
    {{ double }}
    <button @click="increase">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, toRefs, computed, reactive } from "vue";
interface dataProps {
  count: number;
  double: number;
  increase: () => void;
}
export default defineComponent({
  name: "App",
  setup() {
    const data: dataProps = reactive({
      count: 0,
      increase: () => data.count++,
      double: computed(() => data.count * 2),
    });
    const dataRefs = toRefs(data);
    return {
      ...dataRefs,
    };
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
