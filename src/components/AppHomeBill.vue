<template>
  <div class="col s12 m6 l4">
    <div class="card light-blue lighten-2 bill-card">
      <div class="card-content white-text">
        <span class="card-title">Счет в валюте</span>
        <p
          v-for="cur in currencies"
          :key="cur"
          class="currency-line">
          <span>{{ getCurrency(cur) }}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: ['rates'],
  data () {
    return {
      currencies: ['RUB', 'USD', 'EUR']
    }
  },
  computed: {
    base () {
      return this.$store.getters.info.bill / (this.rates.RUB / this.rates.EUR)
    }
  },
  methods: {
    getCurrency (cur) {
      const bill = (this.base * this.rates[cur]).toFixed(2)
      return new Intl.NumberFormat('ru-RU', {
        style: 'currency',
        currency: cur
      }).format(bill)
    }
  }
}
</script>
