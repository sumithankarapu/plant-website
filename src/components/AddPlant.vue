<template>
  <div style="padding-top:15px">
    <form @submit="onSubmit" class="p-formgroup-inline" id ="form-bg">
      <div class="p-field">
        <label for="name" class="p-sr-only">Name</label>
        <InputText v-model="name" id="name" type="text" placeholder="Name" />
        
      </div>
      <div class="p-field">
        <label for="description" class="p-sr-only">Description</label>
        <InputText v-model="description" id="description" type="text" placeholder="Description" />
      </div>
      <div class="p-field">
        <label for="url" class="p-sr-only">URL</label>
        <InputText v-model="url" id="url" type="text" placeholder="Image URL" />
      </div>
      <div id="save-button">
        <Button type="submit" label="Save" />
      </div>  
    </form>
  </div>
</template>

<script>
export default {
  name: "AddPlant",
  data() {
    return {
      name: "",
      description: "",
      url: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      const newPlant = {
        name: this.name,
        description: this.description,
        url: this.url,
        isFavorite: false,
      };

     
      this.$emit("add-plant", newPlant);

      this.name = "";
      this.description = "";
      this.url = "";
    },
  },
};
</script>

<style>
  #form-bg{
    margin:0px;
    display: flex;
    justify-content:center;
    align-items: center;
  }
  #save-button{
    margin-bottom:15px;
  }
</style>
