<template>
  <div class="menu">
    <el-tabs :tab-position="tabPosition" v-loading="loading">
      <el-tab-pane label="Actor's List">
        <Actors :actors="actorsFromDB"/>
      </el-tab-pane>
      <el-tab-pane label="Add an actor">
        <Add @add-actor="addActor"/>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import axios from "axios";
import Add from "./Add.vue";
import Actors from "./Actors.vue";

export default {
  name: "Menu",

  components: {
    Add,
    Actors
  },

  data() {
    return {
      tabPosition: "left",
      loading: true,
      actorsFromDB: []
    };
  },

  created() {
    axios.get("http://localhost:8081/actors").then(response => {
      this.actorsFromDB = response.data;
      this.loading = false;
    });
  },

  methods: {
    addActor(newActor) {
      newActor.films = [];
      this.actorsFromDB.push(newActor);
    }
  }
};
</script>

<style>
.menu {
  margin-top: 2em;
}
</style>
