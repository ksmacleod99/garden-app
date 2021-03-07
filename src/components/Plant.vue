<template>
    <div class="card">
        <h3 class="title">{{ plant.name }}</h3>
        <p>{{plant.id}}</p>
    </div>
</template>

<script>
export default {
    name: "Plant",
    props: {
        plant: Object
    },
}
</script>

<style scoped>
    .card{
        background-color: #fff;
        border-color: slategray;
        padding: 1em;
        margin: 1em;
    }
    .title{
        color: darkolivegreen;
        font-weight: bold;
        font-size: 1em;
    }

</style>