<template>
  <main>
      <div class="container">

            <div class="row py-3" v-if="movies.length > 0">
                <h2 class="text-center m-3">FILM</h2>
                <Video v-for="movie in movies" :key="movie.id" :film="movie" />
            </div>

            <div class="row py-3" v-if="series.length > 0">
                <h2 class="text-center m-3">SERIE TV</h2>
                <Video v-for="serie in series" :key="serie.id" :film="serie" />
            </div>

            <div class="row py-3" v-if="popular.length > 0">
                <h2 class="text-center m-3">POPOLARI</h2>
                <Video v-for="item in popular" :key="item.id" :film="item" />
            </div>
       </div> 
  </main>
</template>

<script>
import Video from "./Video.vue";
export default {
    name: 'Main',
    props:{
        movies: Array,
        series: Array,
        popular: Array,
    },
    components:{
        Video,
    },

    data(){
        return{

        }
    },
}
</script>

<style lang="scss">
    main{
        min-height: calc(100vh - 100px);
        background-color: #202024;
        
        h2{
            font-weight: bold;
            color: #eb0000;
        }
    }
</style>