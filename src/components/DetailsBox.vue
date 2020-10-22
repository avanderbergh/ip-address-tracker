<template>
  <section>
    <div>
      <h2>IP Address</h2>
      <h1>{{ details.ip }}</h1>
    </div>
    <div>
      <h2>Localtion</h2>
      <h1>{{ details.location?.city }}</h1>
    </div>
    <div>
      <h2>Timezone</h2>
      <h1>{{ details.location?.timezone }}</h1>
    </div>
    <div>
      <h2>ISP</h2>
      <h1>{{ details.isp }}</h1>
    </div>
  </section>
</template>

<script>
export default {
  name: "DetailsBlock",
  props: {
    details: Object,
  },
};
</script>

<style scoped>
section {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 1rem;
  background: #fff;
  padding: 1em;
  position: absolute;
  top: -50px;
  left: 10vw;
  right: 10vw;
  border-radius: 0.5em;
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.2);
  z-index: 999;
  min-height: 6em;
}

section > div {
  padding: 0.5em;
}

h1 {
  color: hsl(0, 0%, 17%);
}

h2 {
  font-size: 1rem;
  color: hsl(0, 0%, 59%);
  text-transform: uppercase;
  margin-bottom: 0.5em;
}

@media screen and (min-width: 959px) {
  section > div:not(:last-child) {
    border-right: 1px solid hsl(0, 0%, 59%);
  }
}

@media screen and (max-width: 960px) {
  section {
    grid-template-columns: 1fr;
    text-align: center;
  }
}
</style>