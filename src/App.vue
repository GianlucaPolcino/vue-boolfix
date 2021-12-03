<template>
  <div>
    <Header @search="searchToMain" />
    <Main :movies="movies" :series="series" :popular="popular"/>
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
      popular: [],
      
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
          console.log(this.movies);
        })
      .catch(e =>{
          console.log(e);
        })

        this.popular = [];
      },

      searchPopular(){
        axios.get("https://api.themoviedb.org/3/movie/popular?api_key=e99307154c6dfb0b4750f6603256716d")
      .then(r =>{
          this.popular = r.data.results;
          console.log(this.popular);
        })
      .catch(e =>{
          console.log(e);
        })
      }
    },

    mounted(){
      this.searchPopular()
    }
  }

</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";

</style>
