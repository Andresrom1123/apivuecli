<template>
    <div class="d-flex mt-5 mb-5">
        
        <div class="col-6 pr-0  d-flex flex-column align-items-sm-center">
            <div class="col-11">
                <h1>{{product.name}}</h1>
                <p class="">{{product.description}}</p>
            </div>
            <div class="d-flex">
                <a class="text-muted border border-secondary px-3 pt-3" target="_blank" :href="product.url">Visit Web Site</a>
                <p class="mt-3 px-5 text-muted">Share <i class=" ico fab fa-facebook"></i>  <i class=" ico fab fa-twitter-square"></i></p>
            </div>
        </div>
        <div class=" scroll pr-0 pt-0 mr-5" style="overflow: auto;  height: 600px">
                <img class="marco" :src="product.image" width="100%"><img>
        </div>

    </div>
</template>
<script>
export default {
created() {
      this.getProduct()
  },
  methods: {
      getProduct() {
       const urlProduct = this.baseUrlApi + 'products/' + this.$route.params.id

        axios.get(urlProduct)
            .then(response => {
                this.product = response.data
                console.log(this.product)
            })
            .catch(error => {
                console.log(error.response)
                alert('Tuvimos un error cargando la información')
            })
      }
  },
  data() {
      return {
        product: [],
        baseUrlApi: 'http://fundamentos.academlo.com/api/v1/'
      }
  }    
}
</script>