<template>
  <input type="number" @input="changeAmount($event.target.value)" placeholder="Enter the number" />
</template>

<script>
export default {
  name: 'TheInput',
  props: {
    changeAmount: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style scoped>
input {
  outline: none;
  width: 500px;
  position: relative;
  top: -60px;
  font-size: 1.2em;
  border-radius: 3px;
  border: 0px;
  padding: 10px 15px;
  background: #fafafa;
  color: #333;
}
</style>
