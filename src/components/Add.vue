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
import axios from 'axios'

export default {
    name: 'Add',

    data() {
        return {
            form: {
                firstName: '',
                lastName: '',
            },
            response: ''
        }
    },

    methods: {
        onSubmit() {
            axios({
                method: 'POST',
                url: 'http://localhost:8081/actors',
                data: JSON.stringify({firstName: this.form.firstName, lastName: this.form.lastName}),
                config: {
                    headers: {'Content-Type': 'application/json' }}
                })
                .then(function (response) {
                    console.log(response);
                });
        }
    }
}
</script>

<style>
.add {
    margin-left: 2em;
    margin-right: 2em;
}
</style>