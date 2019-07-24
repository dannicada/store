<template>
    <div>
    <product-form 
    @save-product="addProduct" 
    :model="model" 
    :items="manufacturers">
    </product-form>
    </div>
</template>

<script>
import ProductFrom from '@/components/product/ProductForm.vue'

export default {
  data () {
        return {
          model: {},
          manufacturers: [
            {
              _id: 'sam',
              name: 'Samsung',
            },
            {
              _id: 'apple',
              name: 'Apple',
            },  
          ],
        }
 },
  methods: {
  addProduct (model) {
    console.log('model', model)
  }
  },  
  components: {
    'product-form': ProductFrom
  }
}
</script>