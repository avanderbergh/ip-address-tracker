<template>
  <input
    type="text"
    :value="value"
    @input="$emit('update:value', $event.target.value)"
    v-bind:placeholder="placeholder"
  />
  <input type="submit" v-bind:value="buttonText" />
</template>

<script>
export default {
  props: {
    placeholder: String,
    buttonText: String,
    value: String,
  },
};
</script>

<style scoped>
input {
  border-radius: 0.5em;
  border: none;
}

input[type="submit"] {
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  color: #fff;
  background: #000;
  border-radius: 0 0.25em 0.25em 0;
  cursor: pointer;
  font-size: 2em;
  line-height: 1;
  padding: 0 1em;
  font-weight: 700;
}

input[type="text"] {
  padding: 1em;
  width: 100%;
  font-size: 18px;
}
</style>