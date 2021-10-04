<template>
  <div id = "bg-container">
    <AddPlant @add-plant="addPlant" />
    <Plants @remove-plant="removePlant" @add-favorite="addFavorite" :plants="plants" />
  </div>  
</template>

<script>
import Plants from "../components/Plants";
import AddPlant from "../components/AddPlant";

export default {
  name: "Home",
  components: { AddPlant, Plants },
  methods: {
   
    async addPlant(plant) {
      const res = await fetch(
        "https://61497977035b3600175ba2c4.mockapi.io/plants",
        {
          method: "POST",
          headers: {
            "Content-type": "application/json",
          },
          body: JSON.stringify(plant),
        }
      );

      const data = await res.json();
      this.plants = [...this.plants, data];
    },
   
    async removePlant(id) {
      if (confirm("Are you sure you want to remove this plant?")) {
        const res = await fetch(
          `https://61497977035b3600175ba2c4.mockapi.io/plants/${id}`,
          {
            method: "DELETE",
          }
        );

        res.status === 200
          ? (this.plants = this.plants.filter((plant) => plant.id !== id))
          : alert("Delete failed!");
      }
    },
 
    async addFavorite(id) {
     
      const addFavorite = await this.fetchPlant(id);
      const updatedFavorite = {
        ...addFavorite,
        isFavorite: !addFavorite.isFavorite,
      };

      const res = await fetch(
        `https://61497977035b3600175ba2c4.mockapi.io/plants/${id}`,
        {
          method: "PUT",
          headers: {
            "Content-type": "application/json",
          },
          body: JSON.stringify(updatedFavorite),
        }
      );
      const data = await res.json();

      this.plants = this.plants.map((plant) =>
        plant.id === id ? { ...plant, isFavorite: data.isFavorite } : plant
      );
    },
    async fetchPlants() {
      const res = await fetch(
        "https://61497977035b3600175ba2c4.mockapi.io/plants"
      );
      const data = await res.json();
      return data;
    },
    async fetchPlant(id) {
      const res = await fetch(
        `https://61497977035b3600175ba2c4.mockapi.io/plants/${id}`
      );
      const data = await res.json();
      return data;
    },
  },
  data() {
    return {
      plants: [],
    };
  },
  async created() {
    this.plants = await this.fetchPlants();
  },
};
</script>
<style>
  body {
  margin: 0;
}

  #bg-container{
    
    background-color:#def3d6;
  }
</style>
