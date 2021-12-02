<template>
  <div class="col-3 my-3 text-center poster flip-card">

    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img class="py-3" :src="`https://image.tmdb.org/t/p/w342/${film.poster_path}`" alt="">
      </div>

      <div class="flip-card-back">
        <div class="text-center p-3">
          <h5 v-if="film.name">{{film.name}}</h5>
          <h5 v-else>{{film.title}}</h5>
        </div>

        <div class="text-center p-3">
          <h5 v-if="film.original_name">{{film.original_name}}</h5>
          <h5 v-else>{{film.original_title}}</h5>
        </div>

        <div>
          <country-flag v-if="film.original_language == 'it'" country='it' size='normal'/>
          <country-flag v-else-if="film.original_language == 'en'" country='us' size='normal'/>
          <country-flag v-else-if="film.original_language == 'fr'" country='fr' size='normal'/>
          <country-flag v-else-if="film.original_language == 'es'" country='es' size='normal'/>
          <country-flag v-else-if="film.original_language == 'de'" country='de' size='normal'/>
          <country-flag v-else-if="film.original_language == 'ja'" country='jp' size='normal'/>
          <country-flag v-else-if="film.original_language == 'nl'" country='nl' size='normal'/>
          
          <h5 v-else>{{film.original_language}}</h5>
        </div>

        <div>
          <h5 v-if="film.vote_average == '0'">Nessuna valutazione</h5>
          <h5 v-else>{{film.vote_average}}</h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CountryFlag from "vue-country-flag"
export default {
  name: "Video",
  props:{
    film: Object,
  },

  components:{
    CountryFlag,
  }
  

}
</script>

<style lang="scss">
  .poster{
    min-height: 400px;
    background-color: black;
    color: white;

    img{
      width: 100%;
    }
  }

  /* The flip card container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 200px;
  // border: 1px solid #f1f1f1;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: black;
  color: black;
}

/* Style the back side */
.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
}
</style>