<template>
  <div class="add">
    <el-card class="box-card" shadow="hover">
      <el-row :gutter="20">
        <el-form ref="form" :model="form">
          <el-col :span="12">
            <el-form-item label="First Name">
              <el-input v-model="form.firstName"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="Last Name">
              <el-input v-model="form.lastName"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="24">
            <el-form-item>
              <el-button type="primary" @click="onSubmit">Add Actor</el-button>
            </el-form-item>
          </el-col>
        </el-form>
      </el-row>
    </el-card>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Add",

  data() {
    return {
      form: {
        firstName: "",
        lastName: ""
      },
      errors: []
    };
  },

  methods: {
    onSubmit() {
      if (this.form.firstName.length > 0 && this.form.lastName.length > 0) {
        axios({
          method: "POST",
          url: "http://localhost:8081/actors",
          data: {
            firstName: this.form.firstName.toUpperCase(),
            lastName: this.form.lastName.toUpperCase()
          },
          config: {
            headers: { "Content-Type": "application/json" }
          }
        })
          .then(response => {
            this.$notify({
              title: "Actor Added",
              message: "It's now at the end of the list.",
              type: "success"
            });
            this.form.firstName = "";
            this.form.lastName = "";
            this.$emit("add-actor", response.data);
          })
          .catch(error =>
            this.$notify.error({
              title: "Error",
              message: "There was an error: " + error.message
            })
          );
      }
      else {
        this.$notify({
          title: "Fields Needed",
          message: "You must fill all the fields.",
          type: "warning"
          });
      }
    }
  }
};
</script>

<style>
.add {
  margin-left: 2em;
  margin-right: 2em;
}

.el-notification,
.right {
  font-family: "Avenir", Helvetica, Arial, sans-serif !important;
}
</style>