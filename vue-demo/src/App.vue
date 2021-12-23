<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p>{{ value }}</p>
  <p>{{ state.value }}</p>
  <Calculator msg="Welcome to Your Vue.js + TypeScript App" />
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from "vue";
import Calculator from "./components/Calculator.vue";

export default defineComponent({
  name: "App",
  components: {
    Calculator,
  },
  setup() {
    const value = ref(0);
    const state = reactive({
      value: 0,
    });

    console.log(value);
    return {
      value,
      state,
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
