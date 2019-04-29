<template>
    <el-menu class="el-menu-demo" mode="horizontal">
        <el-menu-item index="1"> Actors </el-menu-item>
    </el-menu>
</template>

<script>
export default {
    name: 'Nav',

    data() {
        return {

        }
    },

    munted() {
        console.log("Component mounted");
    },

    creted() {
        console.log("Component created")
    },

    methods: {
        updateActors() {
        }
    }
    
}
</script>