<template>
  <div id="app">
    <Nav/>
    <Menu/>
  </div>
</template>

<script>
import Nav from './components/Nav.vue'
import Menu from './components/Menu.vue'

export default {
  name: 'app',

  components: {
    Nav,
    Menu
  },

  data() {
    return {

    }
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
}
</style>
