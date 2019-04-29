<template>
<div class="actors">
    {{ actors }}
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
            myActors: []
        }
    },

    munted() {
        console.log("Component mounted");
    },

    creted() {
        console.log("Component created")
    }
    
}
</script>

<style scoped>

</style>
