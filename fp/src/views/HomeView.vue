<template>
  <div class="home">
    <!--<img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
        <header>
          <div class="title">My personal costs</div>
        </header>
        <main>
      <PaymentsDisplay :items="paymentsList"/>
      <AddPaymentForm @addNewPayment="addPaymentData" />
    </main>
  </div>
</template>

<script>

import PaymentsDisplay from "@/components/PaymentsDisplay.vue";
import AddPaymentForm from "@/components/AddPaymentForm.vue";

export default {
  name: 'HomeView',
  components: {
    PaymentsDisplay,
    AddPaymentForm,
  },

  data() {
    return {
      paymentsList: [],
    };
  },

  methods: {
    addPaymentData(data) {
      this.paymentsList.push(data)
    },

    fetchData() {
      return [
        {
          date: "28.03.2020",
          category: "Food",
          value: 169,
        },
        {
          date: "24.03.2020",
          category: "Transport",
          value: 360,
        },
        {
          date: "24.03.2020",
          category: "Food",
          value: 532,
        },
      ];
    },
  },

  created() {
    this.paymentsList = this.fetchData()
  },


  mounted() {
  },
};

</script>



<style lang="scss" scoped>
.title {
  font-size: 20px;
  margin: 0 0 20px 0;
}
</style>
