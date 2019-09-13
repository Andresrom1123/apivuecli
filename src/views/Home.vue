<template>
  <div class="">
    <div class=" mb-5 bg-warning">
        <div class="p-5 ">
            <div class="pt-5 pr-5 pl-5">
                <h1>Los mejores recursos del Marketing Digital <br>
                    Descubre, Aprende, Crece</h1>
            </div>
            <div class="pb-5">
              <button type="button" class="btn btn-light"><router-link class="text-muted text-decoration-none" to="/Categorie">Browse</router-link></button>
            </div>
        </div>
    </div>

    
    <div class="container mt-5 pt-5 mb-5">
        <h3 class="ml-3 pb-3 font-weight-bold">Productos</h3>
        <div class="row m-0 ">
          <div class="col-sm-12 col-lg-4 mb-5" v-for="product in categorieProduct" :key="product.id">
            <featured :url="product.url" :uuid="product.uuid" :name="product.name" :image="product.image" :description="product.description" ></featured>
          </div>
        </div>
      </div>

    <div class="container">
        <div class="container-fluid ">
            <div class="ml-3">
                <h3 class="font-weight-bold">Categories</h3>
                <form class="form-inline row m-0">
                    <input class="form-control form-control-sm w-75 col-11 border border-top-0 border-left-0 border-right-0" type="text"
                        placeholder="Browse Categories" aria-label="Browse Categories">
                    <i class=" fas fa-search " aria-hidden="true"></i>
                </form>
            </div>
            <div class="row m-0 mt-2 mb-2" >
              <div class="col-sm-6 col-lg-3 m-0 box-si  mb-4" v-for="(category, index) in categorie" :key="category.id">
               <categorie v-if="index < 8" :name="category.name" :uuid="category.uuid"></categorie>
              </div>
            </div>
        </div>
    </div>



  </div>

  
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Featured from '@/components/Featured.vue'
import Categorie from '@/components/Categorie.vue'
export default {
  name: 'home',
  components: {
    HelloWorld,
    Featured,
    Categorie
  },
  created() {
      this.getCategorieProduct()
      this.getCategorie()
  },
  methods: {
      getCategorieProduct() {
       const urlCategorieProduct = this.baseUrlApi + "categories/dc2f25dc-a8eb-4a25-8fa5-679027f2ae00/products"

        axios.get(urlCategorieProduct)
            .then(response => {
                this.categorieProduct = response.data.products
                console.log(this.categorieProduct)
            })
            .catch(error => {
                console.log(error.response)
                alert('Tuvimos un error cargando la información')
            })
      },
      getCategorie() {
       const urlCategorie = this.baseUrlApi + "directories/88339b10-0936-4766-ab71-d56e66823cd5/categories"

        axios.get(urlCategorie)
            .then(response => {
                this.categorie = response.data.categories
                console.log(this.categorie)
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
        categorie: [],
        baseUrlApi: 'http://fundamentos.academlo.com/api/v1/'
      }
  }
}
</script>
