<template>
  <h1>crypto</h1>
  <TheInput />
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
