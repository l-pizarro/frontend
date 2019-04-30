<template>
    <div class="menu">
        <el-tabs :tab-position="tabPosition">
            <el-tab-pane label="Actor's List" v-loading="loading">
                <Actors :actors="actorsFromDB"/>
            </el-tab-pane>
            <el-tab-pane label="Add an actor">
                <Add/>
            </el-tab-pane>
        </el-tabs>
    </div>
</template>

<script>
import axios from 'axios'
import Add from './Add.vue'
import Actors from './Actors.vue'

export default {
    name:'Menu',

    components: {
        Add,
        Actors
    },

    data() {
        return {
            tabPosition: 'left',
            loading: true,
            actorsFromDB: []
        };
    },

    created() {
        axios.get('http://localhost:8081/actors').
        then( (response) => {
            this.actorsFromDB = response.data;
            this.loading = false;
            });
    }
};
</script>

<style>
    .menu {
        margin-top: 2em;
    }
</style>
