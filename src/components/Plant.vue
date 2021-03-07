<template>
  <div class="wrapper">
    <div class="info">
      <h3 class="title">{{ plant.name }}</h3>
      <p>{{ plant.id }}</p>
      <p>Is it a weed? {{ plant.weed }}</p>
      <p>Can I eat it? {{ plant.edible }}</p>
      <p>Sun needs: {{ plant.sun }}</p>
      <p>Description: {{ plant.description }}</p>
    </div>

    <div class="controls">
      <i @click="$emit('edit-plant', plant.id)" class="fas fa-pen icon"></i>
      <i
        @click="$emit('delete-plant', plant.id)"
        id="deletePlant"
        class="fas fa-times icon"
      ></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Plant",
  props: {
    plant: Object
  }
};
</script>

<style scoped>
.wrapper {
  background-color: #fff;
  border-color: slategray;
  padding: 1em;
  margin: 1em;
  display: flex;
  width: 80%
}
.info {
  width: 80%;
}
.title {
  color: darkolivegreen;
  font-weight: bold;
  font-size: 1em;
}
.controls {
  max-width: 20%;
  align-content: right;
}
.icon {
  padding: 10px;
  margin: 10px;
}
</style>
