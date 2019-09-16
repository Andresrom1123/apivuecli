<template>
<div class="container">
    <div class="container-fluid ">
        <div class="ml-3">
            <h3>Categories</h3>
            <form class="form-inline row m-0">
                <input class="form-control form-control-sm w-75 col-11 border border-top-0 border-left-0 border-right-0" type="text"
                    placeholder="Browse Categories" aria-label="Browse Categories">
                <i class="fas fa-search " aria-hidden="true"></i>
            </form>
        </div>
        <div class="row m-0 mt-2 mb-2" >
            <div class="col-sm-6 col-lg-3 m-0 box-si  mb-4" v-for="category in categorie" :key="category.id">
            <categorie :name="category.name" :uuid="category.uuid"></categorie>
            </div>
        </div>
    </div>
</div>
</template>
<script>
import Categorie from '@/components/Categorie.vue'
export default {
    components:{
        Categorie
    },
  created() {
      this.getCategorie()
  },
  methods: {
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
        categorie: [],
        baseUrlApi: 'http://fundamentos.academlo.com/api/v1/'
      }
  }
}
</script>