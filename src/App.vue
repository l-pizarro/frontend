<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="container">
      <div class="row">
        <div class="col-6">
          <Actors :actors="actorsFromDB"/>
        </div>
        <div class="col-6">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Actors from './components/Actors.vue'
import axios from 'axios'

export default {
  name: 'app',

  components: {
    Actors,
    HelloWorld
  },

  data() {
    return {
      actorsFromDB: []
    }
  },

  created() {
     axios.get('http://localhost:8081/actors')
        .then( (response) => {
            this.actorsFromDB = response.data;
            }
            );
  },

  mounted() {
    axios.get('http://localhost:8081/actors')
        .then( (response) => {
            this.actorsFromDB = response.data;
            }
            );
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
  margin-top: 60px;
}
</style>
