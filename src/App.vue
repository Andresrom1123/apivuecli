<template>
  <div id="app">
     
    <c-header></c-header>

    <router-view/>
    
    <c-footer></c-footer>
  </div>
</template>
<script>
import CFooter from '@/components/Footer.vue'
import CHeader from '@/components/CHeader.vue'
export default {
  components:{
    CFooter,
    CHeader
  } 
}
</script>
<style>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
