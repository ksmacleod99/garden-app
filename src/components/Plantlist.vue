<template>
  <div class="container">
    <div :key="plant.id" v-for="plant in plants">
      <Plant 
        @edit-plant ="$emit('edit-plant', plant.id)"
        @delete-plant="$emit('delete-plant', plant.id)"
        :plant="plant" 
      />
    </div>
  </div>
</template>

<script>
import Plant from "./Plant";

export default {
  name: "PlantList",
  props: {
    plants: Array
  },
  components: {
    Plant
  },
  emits: ['edit-plant', 'delete-plant'],
};
</script>

<style scoped>
.container {
  border: red solid 3px;
}
</style>
