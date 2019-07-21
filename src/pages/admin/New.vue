<template>
  <form @submit.prevent="saveProduct">
<v-chip outline color="primary">Name</v-chip>
    <v-text-field
      v-model="name"
      v-validate="'required|max:10'"
      :counter="10"
      :error-messages="errors.collect('name')"
      label="Name"
      data-vv-name="name"
      required
    ></v-text-field>

    <v-chip outline color="primary">Price</v-chip>
    <v-text-field
      v-model="price"
      v-validate="'required'"
      :error-messages="errors.collect('price')"
      label="Price"
      data-vv-name="price"
      required
    ></v-text-field>

    <v-chip outline color="primary">Manufacturer</v-chip>
    <v-select
      v-model="manufacturer"
      v-validate="'required'"
      :items="items"
      :error-messages="errors.collect('manufacturer')"
      label="Manufacturer"
      data-vv-name="manufacturer"
      required
    ></v-select>


<v-chip outline color="primary">Image</v-chip>
    <v-text-field
      v-model="image"
      v-validate="'required|url'"
      :error-messages="errors.collect('image')"
      label="Image"
      data-vv-name="image"
      required
    ></v-text-field>

    <v-text-field
      v-model="description"
      v-validate="'required'"
      :error-messages="errors.collect('description')"
      label="Description"
      data-vv-name="description"
      required
    ></v-text-field>


    
    <v-btn v-if="isEditing" type="submit">Update Product</v-btn>
    <v-btn v-else @click="submit">Add Product</v-btn>
  </form>
</template>

<script>
  export default {
    $_veeValidate: {
      validator: 'new'
    },

    data: () => ({
      name: '',
      email: '',
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4'
      ],
      checkbox: null,
      dictionary: {
        attributes: {
          email: 'E-mail Address'
          // custom attributes
        },
        custom: {
          name: {
            required: () => 'Name can not be empty',
            max: 'The name field may not be greater than 10 characters'
            // custom messages
          },
          select: {
            required: 'Select field is required'
          },
          image: {
            required: 'please insert a valid image url'
          },
          manufacturer: {
            required: 'manufacturer is required'
          },
        }
      }
    }),

    mounted () {
      this.$validator.localize('en', this.dictionary)
    },

    methods: {
      submit () {
        this.$validator.validateAll();
        saveProduct();

      },

    saveProduct() {
      // prints all the errors
      console.log(this.errors);
    },
  

      clear () {
        this.name = ''
        this.email = ''
        this.select = null
        this.checkbox = null
        this.$validator.reset()
      }
    }
  }
</script>



