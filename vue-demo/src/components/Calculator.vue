<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="state.num1" @keyup="addnum()" />+
    <input type="text" v-model="state.num2" @keyup="addnum()" />=
    <input type="text" v-model="state.total" />
  </div>
  <div>
    <h1>定时任务</h1>
    每秒加1:{{ state.counter }}
    <br />
    每秒为增加的2倍:{{ state.doubleCounter }}
  </div>
</template>

<script lang="ts">
import {
  computed,
  defineComponent,
  onMounted,
  onUnmounted,
  reactive,
} from "vue";

export default defineComponent({
  name: "Calculator",
  props: {
    msg: String,
  },
  setup() {
    const state: any = reactive({
      num1: 0,
      num2: 0,
      total: 0,
      counter: 1,
      doubleCounter: computed(() => state.counter * 2),
    });

    let timer: number;
    onMounted(() => {
      timer = setInterval(() => {
        state.counter++;
      }, 10000);
    });
    onUnmounted(() => {
      clearInterval(timer);
    });
    const addnum = () => {
      state.total = Number(state.num1) + Number(state.num2);
    };
    return {
      state,
      addnum,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
