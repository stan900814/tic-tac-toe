<template>
  <div id="app">
    <div id="board">
      <div class="row">
        <Box @click="onclick(0,$event)" :n="n"></Box>
        <Box @click="onclick(1,$event)" :n="n"></Box>
        <Box @click="onclick(2,$event)" :n="n"></Box>
      </div>
      <div class="row">
        <Box @click="onclick(3,$event)" :n="n"></Box>
        <Box @click="onclick(4,$event)" :n="n"></Box>
        <Box @click="onclick(5,$event)" :n="n"></Box>
      </div>
      <div class="row">
        <Box @click="onclick(6,$event)" :n="n"></Box>
        <Box @click="onclick(7,$event)" :n="n"></Box>
        <Box @click="onclick(8,$event)" :n="n"></Box>
      </div>
    </div>
    <div>{{result}}</div>
  </div>
</template>

<script>
import Box from "./components/Box";
export default {
  data() {
    return {
      n: 0,
      arr: Array(9).fill(null),
      result: ""
    };
  },
  methods: {
    onclick(i, e) {
      this.n += 1;
      this.arr[i] = e;
      this.judge(this.arr);
    },
    judge(arr) {
      const lines = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
      ];
      for (let i = 0; i < lines.length; i++) {
        const [a, b, c] = lines[i];
        if (arr[a] && arr[a] === arr[b] && arr[a] === arr[c]) {
          this.result = `winner：${arr[a]}`;
        }
      }
      return null;
    }
  },
  components: {
    Box
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  display: flex;
  text-align: center;
  align-items: center;
  flex-direction: column;
}
.row {
  display: flex;
}
</style>
