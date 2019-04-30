<template>
    <div class="actors">
        <el-card class="box-card" shadow="hover">
            <el-table
            :data="actors.filter(data => !search || data.firstName.toLowerCase().includes(search.toLowerCase()))"
            height="650">
                <el-table-column 
                prop="firstName"
                label="First Name">
                </el-table-column>

                <el-table-column 
                prop="lastName"
                label="Last Name">
                </el-table-column>

                <el-table-column
                align="left">
                    <template slot="header" slot-scope="scope">
                        <el-input
                        class="nonepadding"
                        v-model="search"
                        size="medium"
                        placeholder="Type to search by name"/>
                    </template>
                    <template slot-scope="scope">
                        <el-button
                        size="mini"
                        type="primary"
                        plain>See Films</el-button>
                        <el-button
                        size="mini"
                        type="danger"
                        disabled>Delete</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </el-card>
    </div>
</template>

<script>
export default {
    name: 'Actors',

    props: [
        'actors'
    ],

    data() {
        return {
            myActors: [],
            search: ''
        }
    },
    
    methods: {
        updateActors() {
        }
    }
    
}
</script>

<style>
.actors {
    margin-left: 2em;
    margin-right: 2em;
}
.nonepadding {
    padding: 0px !important;
}
</style>