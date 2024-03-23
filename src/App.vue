<template>
  <h1>crypto</h1>
  <TheInput :changeAmount="changeAmount" :convert="convert" />
  <p v-if="error != ''">{{ error }}</p>
  <div class="selectors">
    <TheSelector :setCrypto="setCryptoFirst" />
    <TheSelector :setCrypto="setCryptoSecond" />
  </div>
</template>

<script>
import TheInput from './components/TheInput.vue';
import TheSelector from './components/TheSelector.vue';
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
    };
  },
  methods: {
    changeAmount(val) {
      this.amount = val;
    },
    setCryptoFirst(val) {
      this.cryptoFirst = val;
    },
    setCryptoSecond(val) {
      this.cryptoSecond = val;
    },
    convert() {
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
