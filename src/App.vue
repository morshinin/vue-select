<template>
  <div id="app">
    <select-component />
  </div>
</template>

<script>
import { SelectComponent } from './components';

export default {
  name: 'App',
  components: {
    SelectComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 300px;
  margin: auto;
}
</style>
