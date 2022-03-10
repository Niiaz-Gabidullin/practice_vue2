<template>
  <div id="app">
    <header :class="[$style.header]">My Personal cost</header>
    <main>
      <PaymentForm @add="onDataAdded" />
      <PaymentsList :items="paymentsList" />
    </main>
  </div>
</template>
<script>
import PaymentForm from "./components/PaymentForm";
import PaymentsList from "./components/PaymentsList";
export default {
  name: "App",
  components: { PaymentsList, PaymentForm },
  data() {
    return {
      paymentsList: [
        {
          date: "12.03.2021",
          category: "Education",
          price: 40,
        },
        {
          date: "13.03.2021",
          category: "Education",
          price: 41,
        },
        {
          date: "14.03.2021",
          category: "Education",
          price: 42,
        },
        {
          date: "15.03.2021",
          category: "Education",
          price: 43,
        },
      ],
    };
  },
  methods: {
    onDataAdded(data) {
      this.paymentsList.push(data);
    },
  },
};
</script>

<style lang="css" module>
.header {
  color: red;
}
</style>
