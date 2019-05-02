<template>
  <div class="films">
    <el-table v-if="films.length != 0" :data="films" style="width: 100%" height="250">
      <el-table-column prop="title" label="Title" width="250"></el-table-column>
      <el-table-column prop="releaseYear" label="Release" width="80"></el-table-column>
      <el-table-column prop="description" label="Description"></el-table-column>
    </el-table>
    <el-alert v-else title="This actor has not participated in a movie yet." type="warning"></el-alert>
  </div>
</template>

<script>
export default {
  name: "Films",

  props: ["films"],

  data() {
    return {};
  }
};
</script>

<style>
.films {
  width: 100%;
  max-height: 600px;
  overflow-y: scroll;
}
.el-table .cell {
  word-break: break-word !important;
}
.noFilms {
  color: #e6a23c;
}
</style>