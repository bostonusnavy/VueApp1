<template>
  <div id="app">
      <testComponent>
      </testComponent>
  </div>
</template>

<script>
import testComponent from './components/Test';

export default {
  name: 'App',
  components: {
    testComponent,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
