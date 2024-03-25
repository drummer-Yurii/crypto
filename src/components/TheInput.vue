<template>
  <input
    min="0"
    type="number"
    @input="changeAmount($event.target.value)"
    placeholder="Enter the number"
  />
  <br />
  <button @click="convert()">Convert</button>
  <button @click="favorite()" class="fav-button">Favorite</button>
</template>

<script>
export default {
  name: 'TheInput',
  props: {
    changeAmount: {
      type: Function,
      required: true,
    },
    convert: {
      type: Function,
      required: true,
    },
    favorite: {
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

button {
  position: relative;
  top: -30px;
  padding: 15px 20px;
  color: #fff;
  text-transform: uppercase;
  cursor: pointer;
  background: #1a032d;
  border: 0;
  border-radius: 3px;
}

button.fav-button {
  margin-left: 20px;
}
</style>
