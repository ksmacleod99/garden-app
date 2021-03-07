<template>
  <div class="wrapper">
    <div class="info">
      <h3 class="title">{{ plant.name }}</h3>
      <span v-show="isEditing">
        <input v-model="name" type="text" />
      </span>
      <p><span class="label">Is it a weed? </span>{{ plant.weed }}</p>
      <span v-show="isEditing">
        <input
        type="radio"
        :value="true"
        v-model="weed"
       />
      <label>Yes</label>
      <br />
      <input
        type="radio"
        :value="false"
        v-model="weed"
      />
      <label>No</label>
      </span>
      <p><span class="label">Can I eat it? </span> {{ plant.edible }}</p>
      <span v-show="isEditing">
        <input type="radio" :value="true" v-model="edible" />
        <label>Yes</label>
        <br />
       <input type="radio" :value="false" v-model="edible" />
       <label>No</label>
      </span>
      <p><span class="label">Sun needs: </span>{{ plant.sun }}</p>
      <span v-show="isEditing">      
        <select v-model="sun">
          <option disabled value="">Please select one</option>
          <option value="Full Sun">Full Sun</option>
          <option value="Part Sun">Part Sun</option>
          <option value="Part Shade">Part Shade</option>
          <option value="Full Shade">Full Shade</option>
        </select>
      </span>
      <p><span class="label">Description: </span>{{ plant.description }}</p>
      <span v-show="isEditing">
        <textarea v-model="description" cols="70" rows="10"></textarea>
      </span>
    </div>

    <div class="controls">
      <i v-if="!isEditing" @click="editMode" class="fas fa-pen icon"></i>
      <i v-show="isEditing" @click="closeEdit" class="fas fa-times icon"></i>
      <i v-show="isEditing" @click="[$emit('edit-plant', plant.id), closeEdit]" class="fas fa-save"></i>
      <i
        @click="$emit('delete-plant', plant.id)"
        id="deletePlant"
        class="fas fa-trash icon"
      ></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Plant",
  props: {
    plant: Object
  },
  data () {
    return {
      isEditing: false,
    };
  },
  methods: {
    editMode() {
      this.isEditing = true
    },
    closeEdit() {
      this.isEditing = false
      console.log("close")
    },
    saveEdit(e){
      e.preventDefault() 
      const editPlant = {
        name: this.name,
        weed: this.weed,
        edible: this.edible,
        sun: this.sun,
        description: this.description
      },

     /* this.$emit("edit-plant", editPlant);

      this.name = " ";
      this.weed = false;
      this.edible = false;
      this.sun = " ";
      this.description = " "; 
      
      This is where I left off and where it starts throwing errors */
    }
  },

};
</script>

<style scoped>
.wrapper {
  background-color: #fff;
  border-color: slategray;
  padding: 1em;
  margin: 1em;
  display: flex;
  width: 80%;
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
.label{
  font-weight: bold;
  padding: 10px;
}
</style>
