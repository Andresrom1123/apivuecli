<template>
    <div>
        <div class="container mt-5 pt-5 mb-5">
            <h3 class="ml-3 pb-3 font-weight-bold">Productos de {{nameCategorieProduct.name}}</h3>
            <div class="row m-0 ">
            <div class="col-sm-12 col-lg-4 mb-5" v-for="product in categorieProduct" :key="product.id">
                <featured :url="product.url" :uuid="product.uuid" :name="product.name" :image="product.image" :description="product.description" ></featured>
            </div>
            </div>
        </div>
    </div>
</template>
<script>
import Featured from '@/components/Featured.vue'
export default {
    components: {
        Featured
    },
  created() {
      this.getCategorieProduct()
  },
  methods: {
      getCategorieProduct() {
       const urlCategorieProduct = this.baseUrlApi + 'categories/' + this.$route.params.id + '/products'

        axios.get(urlCategorieProduct)
            .then(response => {
                this.categorieProduct = response.data.products
                this.nameCategorieProduct = response.data
                console.log(this.nameCategorieProduct)
            })
            .catch(error => {
                console.log(error.response)
                alert('Tuvimos un error cargando la información')
            })
      }
  },
  data() {
      return {
        categorieProduct: [],
        nameCategorieProduct: [],
        baseUrlApi: 'http://fundamentos.academlo.com/api/v1/'
      }
  }
}
</script>