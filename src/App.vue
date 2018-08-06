<template>
  <div id="app">
    <PaymentPattern/>

  </div>
</template>

<script>
import PaymentPattern from './components/PaymentPattern.vue'

export default {
  name: 'app',
  components: {
      PaymentPattern
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
