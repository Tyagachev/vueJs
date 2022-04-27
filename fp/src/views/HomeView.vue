<template>
  <div class="home">
    <header>
      <div class="title">My personal costs</div>
      <div>Total Price = {{getFullPaymentValue}} </div>
    </header>
    <main>
       <AddPaymentForm />
      <PaymentsDisplay :items="currentElements"/>
      <MyPagination :cur="cur" :length="12" :n="n" @changePage="changePage"/>
    </main>
  </div>
</template>

<script>
import PaymentsDisplay from "@/components/PaymentsDisplay.vue";
import AddPaymentForm from "@/components/AddPaymentForm.vue";
import { mapMutations, mapGetters } from "vuex";
import MyPagination from "@/components/MyPagination.vue";

export default {
  name: "HomeView",
  components: {
    PaymentsDisplay,
    AddPaymentForm,
    MyPagination,
},
  data() {
    return {
      cur: 1,
      n: 3,
    };
  },
  computed: {
    ...mapGetters(['getFullPaymentValue', 'getPaymentsList']),
    currentElements(){
      return this.getPaymentsList.slice(this.n * (this.cur - 1), this.n * (this.cur -1) + this.n)
    }
  },
  methods: {
    ...mapMutations({
      MyMutation: 'setPaymentsListData'
    }),
    addPaymentData(data) {
      this.paymentsList.push(data)
    },
    changePage(p){
      this.cur = p
    this.$store.dispatch('fetchData',p)
    }
  },
  created() {
    this.$store.dispatch('fetchData',this.cur)
    // this.$store.commit('setPaymentsListData', this.fetchData())
  },
  mounted() {
  },
};
</script>

<style lang="scss" scoped>
.title {
  font-size: 20px;
}
</style>
