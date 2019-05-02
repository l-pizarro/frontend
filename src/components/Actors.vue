<template>
  <div class="actors">
    <el-card class="box-card" shadow="hover">
      <el-table
        :data="actors.filter(data => !search || data.firstName.toLowerCase().includes(search.toLowerCase()))"
        :default-sort="{prop: 'actorId', order: 'ascending'}"
        row-key="actorId"
        :expand-row-keys="rowsToExpand"
        height="650"
      >
        <el-table-column prop="actorId" sortable width="150" label="#"></el-table-column>

        <el-table-column prop="firstName" label="First Name"></el-table-column>

        <el-table-column prop="lastName" label="Last Name"></el-table-column>

        <el-table-column type="expand">
          <template slot-scope="props">
            <el-row>
              <el-col :span="20" height="300">
                <Films :films="props.row.films"/>
              </el-col>
            </el-row>
          </template>
        </el-table-column>

        <el-table-column align="left">
          <template slot="header" slot-scope="scope">
            <el-input
              class="nonepadding"
              v-model="search"
              size="medium"
              placeholder="Search by first name"
            />
          </template>
          <template slot-scope="scope">
            <el-button
              v-if="rowsToExpand[0] != scope.row.actorId"
              size="mini"
              type="primary"
              plain
              @click="seeFilms(scope.row.actorId)"
            >See Films</el-button>
            <el-button
              v-else
              size="mini"
              type="primary"
              plain
              @click="closeFilms()"
            >Close Films</el-button>
            <el-button size="mini" type="danger" disabled>Delete Actor</el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-card>
  </div>
</template>

<script>
import Films from "./Films.vue";

export default {
  name: "Actors",

  components: {
    Films
  },

  props: ["actors"],

  data() {
    return {
      loading: true,
      rowsToExpand: [0],
      search: ""
    };
  },

  methods: {
    seeFilms(actorId) {
      this.rowsToExpand.pop();
      this.rowsToExpand.push(actorId);
    },
    closeFilms() {
      this.rowsToExpand.pop();
      this.rowsToExpand.push(0);
    }
  },

  creted() {
    myActors = this.actors;
  }
};
</script>

<style>
.actors {
  margin-left: 2em;
  margin-right: 2em;
}
.nonepadding {
  padding: 0px !important;
}

ul {
  list-style-type: none;
}

.el-collapse {
  border: none !important;
}

.el-collapse-item__header {
  border-top: none !important;
  border-bottom: none !important;
}

.el-table__empty-text {
  display: none;
}

.el-icon-arrow-right:before {
  content: "" !important;
}
</style>