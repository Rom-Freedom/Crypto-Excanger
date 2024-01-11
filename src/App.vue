<template>
  <h1>Crypto</h1>
  <Input :changeAmount="changeAmount" :convert="convert" :favorite="favorite"/>
  <p className="outputErr" v-if="error != ''">{{ error }}</p>
  <p className="outputRes" v-if="result != 0">{{ result }}</p>
  <Favorite :favs="favs" v-if="favs.length > 0" :getFromFavs="getFromFavs"/>
  <div className="selectors">
    <Selector :setCrypto="setcryptoFirst" :cryptoNow="cryptoFirst" />
    <Selector :setCrypto="setcryptoSecond" :cryptoNow="cryptoSecond" />
  </div>
</template>

<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'
import Favorite from './components/Favorite.vue'
import CryptoConvert from 'crypto-convert';

const convert = new CryptoConvert(/*options?*/);

export default {
  components: { Input, Selector, Favorite },
  data() {
    return {
      amount: 0,
      cryptoFirst: '',
      cryptoSecond: '',
      error: '',
      result: 0,
      favs: []
    }
  },
  methods: {
    favorite() {
      this.favs.push({
        from: this.cryptoFirst,
        to: this.cryptoSecond
      });
    },
    getFromFavs(index) {
      this.cryptoFirst = this.favs[index].from
      this.cryptoSecond = this.favs[index].to
    },
    changeAmount(val) {
      this.amount = val
    },
    setcryptoFirst(val) {
      this.cryptoFirst = val
    },
    setcryptoSecond(val) {
      this.cryptoSecond = val
    },
    async convert() {
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
      await convert.ready();

      if(this.cryptoFirst == 'BTC' && this.cryptoSecond == 'ETH')
        this.result = convert.BTC.ETH(this.amount);
      else  if(this.cryptoFirst == 'BTC' && this.cryptoSecond == 'USDT')
        this.result = convert.BTC.USDT(this.amount);
      else  if(this.cryptoFirst == 'ETH' && this.cryptoSecond == 'BTC')
        this.result = convert.ETH.BTC(this.amount);
      else  if(this.cryptoFirst == 'ETH' && this.cryptoSecond == 'USDT')
        this.result = convert.ETH.USDT(this.amount);
      else  if(this.cryptoFirst == 'USDT' && this.cryptoSecond == 'BTC')
        this.result = convert.USDT.BTC(this.amount);
      else  if(this.cryptoFirst == 'USDT' && this.cryptoSecond == 'ETH')
        this.result = convert.USDT.ETH(this.amount);
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

.outputRes {
  font-family: 'Nabla', cursive;
  font-size: 2em;
}
</style>
