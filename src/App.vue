<template>
  <header>
    <h1>IP Address Tracker</h1>
    <form>
      <input
        type="text"
        v-model="ip"
        @keydown="handleInputChanged"
        placeholder="Search for any IP address or domain"
      />
      <input type="submit" value=">" />
    </form>
  </header>
  <h1>{{ ip }}</h1>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  setup() {
    const ip = ref("");

    function handleInputChanged(e) {
      if (!(!isNaN(Number(e.key)) || e.keyCode === 190)) e.preventDefault();
    }
    return { ip, handleInputChanged };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Rubik", sans-serif;
}

header {
  background: url(/pattern-bg.png);
  text-align: center;
  color: #fff;
  padding: 3em;
}

form {
  position: relative;
  margin: 1em;
}

input {
  border-radius: 0.5em;
  border: none;
  padding: 1em;
}

input[type="submit"] {
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  color: #fff;
  background: #000;
  border-radius: 0 0.5em 0.5em 0;
  cursor: pointer;
}

input[type="text"] {
  width: 100%;
  font-size: 18px;
}
</style>
