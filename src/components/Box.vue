<template>
  <div class="suqare" @click="onClick">{{text}}</div>
</template>
<script>
export default {
  props: ["n"],

  data() {
    return {
      text: ""
    };
  },
  methods: {
    onClick() {
      if (this.text !== "") {
        return;
      } else {
        this.text = this.n % 2 === 0 ? "x" : "o";
      }

      this.$emit("click", this.text);
    }
  }
};
</script>
<style >
.suqare {
  border: 2px solid black;
  width: 100px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 80px;
}
</style>