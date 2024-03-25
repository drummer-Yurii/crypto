<template>
  <h1>crypto</h1>
  <TheInput :changeAmount="changeAmount" :convert="convert" :favorite="favorite" />
  <p v-if="error != ''">{{ error }}</p>
  <p v-if="result != 0" class="result-text">{{ result }}</p>
  {{ favs }}
  <div class="selectors">
    <TheSelector :setCrypto="setCryptoFirst" />
    <TheSelector :setCrypto="setCryptoSecond" />
  </div>
</template>

<script>
import TheInput from './components/TheInput.vue';
import TheSelector from './components/TheSelector.vue';
import CryptoConvert from 'crypto-convert';

const convert = new CryptoConvert();
export default {
  name: 'App',
  components: {
    TheInput,
    TheSelector,
  },
  data() {
    return {
      amount: 0,
      cryptoFirst: '',
      cryptoSecond: '',
      error: '',
      result: 0,
      favs: [],
    };
  },
  methods: {
    favorite() {
      this.favs.push({
        from: this.cryptoFirst,
        to: this.cryptoSecond,
      });
    },
    changeAmount(val) {
      this.amount = val;
    },
    setCryptoFirst(val) {
      this.cryptoFirst = val;
    },
    setCryptoSecond(val) {
      this.cryptoSecond = val;
    },
    async convert() {
      if (this.amount <= 0) {
        this.error = 'Enter number more than zero';
        return;
      } else if (this.cryptoFirst == '' || this.cryptoSecond == '') {
        this.error = 'Choose currency first';
        return;
      } else if (this.cryptoFirst == this.cryptoSecond) {
        this.error = 'Choose another currency';
        return;
      }

      this.error = '';
      await convert.ready();

      if (this.cryptoFirst == 'BTC' && this.cryptoSecond == 'ETH') {
        this.result = convert.BTC.ETH(this.amount);
      } else if (this.cryptoFirst == 'BTC' && this.cryptoSecond == 'USDT') {
        this.result = convert.BTC.USDT(this.amount);
      } else if (this.cryptoFirst == 'ETH' && this.cryptoSecond == 'BTC') {
        this.result = convert.ETH.BTC(this.amount);
      } else if (this.cryptoFirst == 'ETH' && this.cryptoSecond == 'USDT') {
        this.result = convert.ETH.USDT(this.amount);
      } else if (this.cryptoFirst == 'USDT' && this.cryptoSecond == 'BTC') {
        this.result = convert.USDT.BTC(this.amount);
      } else if (this.cryptoFirst == 'USDT' && this.cryptoSecond == 'ETH') {
        this.result = convert.USDT.ETH(this.amount);
      }
    },
  },
};
</script>

<style scoped>
.selectors {
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}
</style>
