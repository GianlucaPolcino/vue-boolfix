<template>
  <main>
      <div class="container">
            <div class="row justify-content-center">
                <div class="col" v-for="(movie, index) in movies" :key="index">
                    <ul class="text-center">
                        <li>{{movie.title}}</li>
                        <li>{{movie.original_title}}</li>
                        <li>{{movie.original_language}}</li>
                        <li>{{movie.vote_average}}</li>
                    </ul>
                </div>
            </div>
       </div> 
  </main>
</template>

<script>

export default {
    name: 'Main',
    props:{
        movies: Array,
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
        background-color: gray;

        ul{
            list-style: none;
            
            li{
                color: white;
            }
        } 
        
    }
</style>