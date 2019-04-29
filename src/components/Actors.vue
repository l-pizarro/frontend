<template>
<div class="actors">
    <button class="btn btn-primary">Update Actors</button>
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
    },

    methods: {
        updateActors() {
            axios.get('http://localhost:8081/actors')
        .then( (response) => {
            this.actors = response.data;
            }
            );
        }
    }
    
}
</script>

<style scoped>

</style>
