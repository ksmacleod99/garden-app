<template>
  <div class="home">
    <Header />
    <Plantlist />
  </div>
</template>

<script>
import Header from "../components/Header";
import Plantlist from "../components/Plantlist";

export default {
  name: "Home",
  components: {
    Header,
    Plantlist
  },
  data() {
    return {
      plants: []
    };
  },
  methods: {
    async fetchPlantList() {
      const res = await fetch("http://localhost:5000/plants");
      const data = await res.json();
      return data;
    },
    /* async fetchPlant(id) {
      const res = await fetch(`/api/plants/${id}`);
      const data = await res.json();
      return data;
    }, */
    async created() {
      this.plants = await this.fetchPlantList();
      console.log(this.plants);
    }
  }
};
</script>
