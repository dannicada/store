<template>
  <form @submit.prevent="submit">
<v-chip outline color="primary">Name</v-chip>
    <v-text-field
      v-model="model.name"
      v-validate="'required|max:10'"
      :counter="10"
      :error-messages="errors.collect('name')"
      label="Name"
      data-vv-name="name"
      required
    ></v-text-field>

    <v-chip outline color="primary">Price</v-chip>
    <v-text-field
      v-model="model.price"
      v-validate="'required'"
      :error-messages="errors.collect('price')"
      label="Price"
      data-vv-name="price"
      required
    ></v-text-field>

    <v-chip outline color="primary">Manufacturer</v-chip>
    <v-select
      v-model="model.manufacturer"
      v-validate="'required'"
      :items="manufacturers"
      :error-messages="errors.collect('select')"
      label="Manufacturer"
      data-vv-name="select"
      required

    ></v-select>


<v-chip outline color="primary">Image</v-chip>
    <v-text-field
      v-model="model.image"
      v-validate="'required|url'"
      :error-messages="errors.collect('url')"
      label="Image"
      data-vv-name="url"
      required
      
    ></v-text-field>

    <v-text-field
      v-model="model.description"
      v-validate="'required'"
      :error-messages="errors.collect('text')"
      label="Description"
      data-vv-name="text"
      required
    ></v-text-field>


    
    <v-btn v-if="isEditing" @click="saveProduct">Update Product</v-btn>
    <v-btn v-else @click="saveProduct">Add Product</v-btn>
  </form>
</template>

<script>
  export default {
    props: ['model', 'manufacturers', 'isEditing'],
    methods: {
      saveProduct () {
        this.$validator.validateAll()
        this.$emit('save-product', this.model)
      }
    }
  }
</script>


