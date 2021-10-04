<template>
  <div class="plant">
    <!-- <h3>{{ plant.name }}</h3> -->
    <Card class="plant-card">
      <template #header>
        <img  id ="image" :src="plant.url" alt="Plant" />
      </template>
      
      <template #title>
        
          {{ plant.name }}
        
      </template>
      
      <template #content>
        
        <p>
         {{plant.description}}
        </p>
      </template>
      <template #footer>
      
        <Button
          @click="onRemove(plant.id)"
          icon="pi pi-times"
          label="Remove"
          class="p-button-danger"
          style="margin-right: 4em"
        />
        
        <Button
          @click="$emit('add-favorite', plant.id)"
          icon="pi pi-heart"
          :class="[
            plant.isFavorite ? '' : 'p-button-outlined',
            'p-button-rounded',
            'p-button-success',
          ]"
        />
       
      </template>
       
    </Card>
  </div>
</template>

<script>
export default {
  props: {
    plant: Object,
  },
  components: {},
  methods: {
    onRemove(id) {
      this.$emit("remove-plant", id);
    },
  },
};
</script>

<style>
#image {
  height: 230px;
  object-fit: cover;
  
}

.plant-card{
 
  height:90vh;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
 
  
}


</style>
