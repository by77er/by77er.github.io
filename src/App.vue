<template>
  <div id="app">
    <MainPage/>
  </div>
</template>

<script>
import MainPage from './components/MainPage'

export default {
  name: 'App',
  components: {
    MainPage
  }
}
</script>

<style>
html, body {
  background-color: #101011;
  margin: 0px;
  padding: 0px;
  overflow-x:hidden;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #E8E7DD;
  margin-top: 60px;
}
</style>
