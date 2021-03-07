<template>
    <div class="container" :key="plant.id" v-for="plant in plants">
        <Plant :plant="plant"/>
    </div>
</template>

<script>
import Plant from './Plant'

export default {
    name: "Plantlist",
    props: {
        plants: Array
    },
    components: {
        Plant
    }
}
</script>

<style scoped>
    .container {
        border: red;
    }
</style>