<template>
  <div class="col-xl-3 col-lg-4 col-md-6 my-3 text-center poster flip-card">

    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img v-if="film.poster_path" class="py-3" :src="`https://image.tmdb.org/t/p/w342/${film.poster_path}`" alt="">
        <div class="no-poster py-5" v-else>
          <h3 v-if="film.original_name" class="py-3">{{film.original_name}}</h3>
          <h3 v-else class="py-3">{{film.original_title}}</h3>
          <h4>404: immagine di copertina non trovata!</h4>
        </div>
      </div>

      <div class="flip-card-back">
        <div class="text-center p-3">
          <h4>Titolo:</h4>
          <h5 v-if="film.name">{{film.name}}</h5>
          <h5 v-else>{{film.title}}</h5>
        </div>

        <div class="text-center p-3">
          <h4>Titolo originale:</h4>
          <h5 v-if="film.original_name">{{film.original_name}}</h5>
          <h5 v-else>{{film.original_title}}</h5>
        </div>

        <div>
          <h4>Lingua:</h4>
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
          <h4>Voto:</h4>
          <i v-for="(item, index) in 5" :key="index"
          :class="index < Math.round(film.vote_average / 2) ? 'fas' : 'far'"
          class="fa-star"></i>
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
  @import "~@fortawesome/fontawesome-free/css/all.min.css";

  .poster{
    min-height: 400px;
    background-color: black;
    color: white;

    img{
      width: 240px;
    }

    .no-poster{
      color: white;
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