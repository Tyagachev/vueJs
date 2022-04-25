<template>
  <div class="paymentsList">
    <div class="paymmentItem" v-for="(item, index) in items" :key="index">
      {{ item }}
    </div>
  </div>
</template>

<script>
export default {
  name: "PaymentsDisplay",
  props: {
    items: {
      type: Array,
      default: ()=>[]
    }
  }
}
</script>