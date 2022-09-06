<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <!-- binding object -->
  <div>
    Shopping Mall
    <h4 :style="style">vue clone coding</h4>
    <p>{{ price1 }} dollar</p>
  </div>
  <!-- biding computed -->
  <div>
    <h4 :style="classObject">vue clone coding</h4>
    <p>{{ price2 }} dollar</p>
  </div>

  <!-- Binding to Arrays -->
  <div>
    <h4 :style="[bgColor, color]">vue clone coding</h4>
    <p>{{ price2 }} dollar</p>
  </div>
  <div>
    <h4 :style="[bgColor, { color: style.color }]">vue clone coding</h4>
    <p>{{ price2 }} dollar</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      price1: 60,
      price2: 70,
      //binding object
      style: { backgroundColor: 'black', color: 'red' },
      //biding computed
      hasError: true,
      error: '123',
      //Binding to Arrays
      bgColor: 'backgroundColor:green',
      color: 'color:orange',
    };
  },
  computed: {
    classObject() {
      return {
        backgroundColor: this.hasError ? 'black' : 'red',
        color: this.error === 'true' ? 'red' : 'yellow',
      };
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
