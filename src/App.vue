<template>
  <h1>Crypto</h1>
  <Input :changeAmount="changeAmount" :convert="convert" />
  <p className="outputErr" v-if="error != ''">{{ error }}</p>
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
      cryptoSecond: '',
      error: ''
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
    },
    convert() {
      if(this.amount <= 0) {
        this.error = 'Enter a number more than 0';
        return;
      } else if(this.cryptoFirst == '' || this.cryptoSecond == '') {
        this.error = 'Select the currency';
        return;
      } else if(this.cryptoFirst == this.cryptoSecond) {
        this.error = 'Select the currency to convert properly';
        return;
      }
      this.error = '';
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
