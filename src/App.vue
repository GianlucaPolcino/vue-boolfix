<template>
  <div>
    <Header @search="searchToMain" />
    <Main :movies="movies" :series="series"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from "axios"

export default {
  name: 'App',
  components: {
    Main,
    Header,
    
  },

  data(){
    return{
      headerSearch:'',
      movies: [],
      series: [],
      
    }
  },

  methods:{
    searchToMain(search){
      this.headerSearch = search;
      console.log(this.headerSearch);
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params:{
          api_key:"e99307154c6dfb0b4750f6603256716d",
          lanuage: "it-IT",
          query: this.headerSearch,
        }
      })
      .then(r =>{
          this.movies = r.data.results;
          console.log('dopo', this.headerSearch);
          console.log(this.movies);
        })
      .catch(e =>{
          console.log(e);
        })

        axios.get("https://api.themoviedb.org/3/search/tv", {
        params:{
          api_key:"e99307154c6dfb0b4750f6603256716d",
          lanuage: "it-IT",
          query: this.headerSearch,
        }
      })
      .then(r =>{
          this.series = r.data.results;
          console.log('dopo', this.headerSearch);
          console.log(this.movies);
        })
      .catch(e =>{
          console.log(e);
        })
      },
    },
  }

</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";

</style>
