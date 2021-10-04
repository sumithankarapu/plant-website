<template>
  <div class="p-grid p-jc-around" id="cards-bg-container">
    <div class="p-col-12 p-md-6 p-lg-3" v-for="plant in plants" :key="plant.id">
      <!-- <h3>{{ plant.name }}</h3> -->
      <Plant
        @remove-plant="$emit('remove-plant', plant.id)"
        @add-favorite="$emit('add-favorite', plant.id)"
        :plant="plant"
      />
    </div>
  </div>
</template>

<script>
import Plant from "./Plant";

export default {
  props: {
    plants: Array,
  },
  components: { Plant },
  emits: ["remove-plant", "add-favorite"],
};
</script>

<style>
#cards-bg-container{
  padding:25px;
}
</style>
