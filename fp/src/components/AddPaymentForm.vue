<template>
  <div class="form-wrapper">
    <button class="btn__add" @click = "visible=!visible">+ADD NEW COST</button>

    <div v-show="visible">
    <!--<input v-model="date"  placeholder="date"/>-->
    <input v-model="category" placeholder="category"/>
    <input v-model="value" placeholder="value"/>
    <button @click="onClickSave">Save</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "AddPaymentForm",
  data() {
    return {
      /*date: "",*/
      category: "",
      value: "",
      visible:false,
    }
  },
  computed: {
    getCurrentDate(){
      const today = new Date()
      const shortDate = new Intl.DateTimeFormat("ru", {dateStyle: "short"}).format(today);
      return shortDate
    }
  },
  methods: {
    onClickSave(){
      const data = {
        date: this.date || this.getCurrentDate,
        category: this.category,
        value: this.value
      }
      this.$emit('addNewPayment', data)
      console.log(data);
    }
  },
}
</script>

<style lang="scss">
  .btn__add {
    background-color:#009f95;
    color: white;
    border: none;
    padding: 8px;
    margin: 20px 0 20px 0;
  }
  
</style>
