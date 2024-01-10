<template>
  <h1>Crypto</h1>
  <Input :changeAmount="changeAmount" />
  <div className="selectors">
    <Selector :setCrypto="setcryptoFirst" />
    <Selector :setCrypto="setcryptoSecond" />
  </div>
</template>

<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'

export default {
  components: { Input, Selector },
  data() {
    return {
      amount: 0,
      cryptoFirst: '',
      cryptoSecond: ''
    }
  },
  methods: {
    changeAmount(val) {
      this.amount = val
    },
    setcryptoFirst(val) {
      this.cryptoFirst = val
    },
    setcryptoSecond(val) {
      this.cryptoSecond = val
    }
  }
}
</script>


<style scoped>
.selectors {
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}
</style>
