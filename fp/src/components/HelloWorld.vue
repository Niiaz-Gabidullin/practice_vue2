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
    <label
      ><input type="checkbox" v-model="show" /> отобразить экранную
      клавиатуру</label
    >

    <div v-if="show">
      Виртуальная клавиатура
      <button v-for="btn in 10" :key="btn" @click="inputNam(btn - 1)">
        {{ btn - 1 }}
      </button>
      <button @click="deleteBtn" class="btn">E</button>
    </div>
    <br />
    <label><input type="radio" value="1" v-model="operch" />Операнд 1</label>
    <label><input type="radio" value="2" v-model="operch" />Операнд 2</label>
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
      show: false,
      arr: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      operch: "",
    };
  },
  methods: {
    inputNam(i) {
      const { operch } = this;
      const input = operch === "1" ? "operand1" : "operand2";
      this[input] = +(this[input] += String(i));
    },
    deleteBtn() {
      const { operch } = this;
      const input = operch === "1" ? "operand1" : "operand2";
      this[input] = String(this[input]).slice(0, -1)
    },
    addRes() {
      const { operand1, operand2 } = this;
      this.result = operand1 + operand2;
    },
    multRes(op1, op2) {
      this.result = op1 * op2;
    },
    calcRes() {
      const { operand1, operand2 } = this;
      this.result = operand1 - operand2;
    },
    divRes() {
      const { operand1, operand2 } = this;
      this.result = operand1 / operand2;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  margin-left: 5px;
}
.keyboard {
  margin-bottom: 10px;
}
.radio {
  align-items: center;
}
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
