<template>
  <div>
    <b-container>
      <b-navbar
        type="light"
        variant="light"
      >
        <b-nav-form>
          <b-input-group prepend="Movie Key Word">
            <b-form-input v-model="keyword"></b-form-input>
            <b-button
              variant="outline-primary"
              class="my-2 my-sm-0 ml-2"
              @click="searchMovie(keyword)"
            >Search</b-button>
          </b-input-group>
        </b-nav-form>
      </b-navbar>
      <b-row>
        
          <Movie
            v-for="movie in movies"
            :key="movie.id"
            :title="movie.title"
            :overview="movie.overview"
            :image="movie.poster_src"
          />

      </b-row>

    </b-container>
  </div>
</template>

<script>
import Movie from "./Movie";
import Axios from "axios";

export default {
  components: {
    Movie
  },

  name: "Home",

  mounted() {
    this.searchMovie("z");
  },

  data: () => ({
    movies: [],
    keyword: ""
  }),

  methods: {
    searchMovie(key) {
      this.movies = [];
      Axios.get(
        "movie?api_key=e13394375a09fbd46812b9a5d6e44045&query=" + key
      ).then(res => {
        console.log(res.data.results);
        res.data.results.forEach(item => {
          item.poster_src =
            "https://image.tmdb.org/t/p/w185" + item.poster_path;
          this.movies.push(item);
        });
      });
    }
  }
};
</script>

