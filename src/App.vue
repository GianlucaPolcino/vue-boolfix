<template>
  <div>
    <Header @search="searchToMain" />
    <Main :headerSearch="headerSearch"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"

export default {
  name: 'App',
  components: {
    Main,
    Header,
    
  },

  data(){
    return{
      headerSearch:'',
    }
  },

  methods:{
    searchToMain(search){
      this.headerSearch = search;
      console.log(this.headerSearch);
    }
  }
}
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";

</style>
