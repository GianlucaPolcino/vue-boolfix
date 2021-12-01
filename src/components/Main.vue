<template>
  <main>
      <div class="container">
            <div class="row">
                <div class="col">
                    <ul v-for="(movie, index) in movies" :key="index">
                        <li>{{movie.original_title}}</li>
                        <li>{{movie.vote_average}}</li>
                    </ul>
                </div>
            </div>
       </div> 
  </main>
</template>

<script>
import axios from "axios"

export default {
    name: 'Main',
    props:{
        headerSearch: String
    },

    data(){
        return{
            movies: [],
            test: "matrix",
        }
    },

    methods:{
        getApi(){
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=${this.test}`)
            .then(r =>{
                this.movies = r.data.results;
                console.log('main', this.headerSearch);
            })
            .catch(e =>{
                console.log(e);
            })
        },
    },

    mounted(){
        this.getApi();
    },

    computed:{
    }
}
</script>

<style lang="scss">
    main{
        min-height: calc(100vh - 100px);
        background-color: gray;
    }
</style>