<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <hr />
    <div class="display">
      <input v-model.number="operand1" />
      <input v-model.number="operand2" />
      {{ result }}
    </div>

    <div class="keyboard">
      <button @click="addRes">+</button>
      <button @click="calcRes">-</button>
      <button @click="multRes(operand1, operand2)">*</button>
      <button @click="divRes">/</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
  methods: {
    addRes() {
      const { operand1, operand2 } = this;
      this.result = operand1 + operand2;
    },
    multRes(op1, op2) {
      this.result = op1 * op2;
    },
    calcRes(){
      const { operand1, operand2 } = this;
      this.result = operand1 - operand2;
    },
    divRes(){
      const { operand1, operand2 } = this;
      this.result = operand1 / operand2;
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
