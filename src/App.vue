<template>
  <div id="app">
    <SplashFeed />
  </div>
</template>

<script>
import SplashFeed from './components/SplashFeed'
export default {
  name: 'App',
  components: {
    SplashFeed
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow: hidden;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
</style>
