<template>
  <form @submit="onSubmit">
    <div class="form-control">
      <label>Plant Name</label>
      <input type="text" v-model="name" name="name" placeholder="Plant Name" />
    </div>

    <div class="radio-group">
      <p>Is it a weed?</p>
      <input type="radio" :value="true" v-model="weed" @click="additionalInfo = false" />
      <label>Yes</label>
      <br />
      <input type="radio" :value="false" v-model="weed" @click="additionalInfo = true"/>
      <label>No</label>
    </div>

    <div class="additional radio-group" v-if="additionalInfo">
      <p>Is it edible?</p>
      <input type="radio" :value="true" v-model="edible" />
      <label>Yes</label>
      <br />
      <input type="radio" :value="false" v-model="edible" />
      <label>No</label>
    </div>

    <div class="dropdown">
      <label>Minimum Sun Needs: </label>
      <select v-model="sun">
        <option disabled value="">Please select one</option>
        <option value="Full Sun">Full Sun</option>
        <option value="Part Sun">Part Sun</option>
        <option value="Part Shade">Part Shade</option>
        <option value="Full Shade">Full Shade</option>
      </select>
    </div>

    <div class="textbox">
      <textarea v-model="description" cols="30" rows="10"></textarea>
    </div>

    <input type="submit" value="Save Plant" />
  </form>
</template>

<script>
export default {
  name: "AddPlant",
  data() {
    return {
      name: "",
      weed: true,
      additionalInfo: false,
      edible: false,
      sun: "",
      description: ""
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.name) {
        alert("Add a plant");
        return;
      }
      const newPlant = {
        name: this.name,
        weed: this.weed,
        edible: this.edible,
        sun: this.sun,
        description: this.description
      };

      this.$emit("add-plant", newPlant);

      this.name = " ";
      this.weed = false;
      this.edible = false;
      this.sun = " ";
      this.description = " ";
    }
  }
};
</script>
