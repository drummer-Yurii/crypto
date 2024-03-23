<template>
  <h1>crypto</h1>
  <TheInput :changeAmount="changeAmount" />
  <div class="selectors">
    <TheSelector />
    <TheSelector />
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
    };
  },
  methods: {
    changeAmount(val) {
      this.amount = val;
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
