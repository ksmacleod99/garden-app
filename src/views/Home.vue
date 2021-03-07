<template>
  <div class="home">
    <AddPlant @add-plant="addPlant" />
    <!-- to do: toggle -->
    <Plantlist @delete-plant="deletePlant" :plants="plants" />
  </div>
</template>

<script>
import Plantlist from "../components/Plantlist";
import AddPlant from "../components/AddPlant";

export default {
  name: "Home",
  components: {
    Plantlist,
    AddPlant
  },
  data() {
    return {
      plants: []
    };
  },
  methods: {
    async addPlant(plant) {
      const res = await fetch("api/plants", {
        method: "POST",
        headers: {
          "Content-type": "application/json"
        },
        body: JSON.stringify(plant)
      });
      const data = await res.json();
      this.plants = [...this.plants, data];
    },

    async deletePlant(id) {
      if (confirm("Are you sure?")) {
        const res = await fetch(`api/plants/${id}`, {
          method: "DELETE"
        });
        res.status === 200
          ? (this.plants = this.plants.filter(plant => plant.id !== id))
          : alert("Error Deleting");
      }
    },
    /* async editPlant(id){

    }, */
    async fetchPlantList() {
      const res = await fetch("api/plants");
      const data = await res.json();
      return data;
    },
    async fetchPlant(id) {
      const res = await fetch(`/api/plants/${id}`);
      const data = await res.json();
      return data;
    },
  },
    async created() {
    this.plants = await this.fetchPlantList()
  }
};
</script>

<style scoped>
.home {
  padding: 1em;
  margin: 1em;
  display: inline;
  border: green;
}
</style>
