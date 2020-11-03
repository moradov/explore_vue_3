<template>
  <Container>
    <Controller @fetch-data="fetchData" />
    <div class="movies-list" v-if="movies && movies.length > 0 ">
      <MovieItem
        v-for="movie in movies"
        :key="movie.id"
        :name="movie.title"
        :overview="movie.overview"
        :img_src="movie.poster_path"
      />
    </div>
    <Center>
      <ErrHand v-if="err && !movies.lenght > 0" :loadAgain="()=> fetchData(currentType) " />
      <Spinner v-if="loading" />
    </Center>
  </Container>
</template>

<script>
import axios from "axios";
import KEYS from "./assets/keys";
import Controller from "./components/Controller";
import MovieItem from "./components/MovieItem";
import Container from "./components/layout/Container";
import Spinner from "./components/Spinner";
import ErrHand from "./components/ErrHand";
// import Center from "./components/layout/Center";
export default {
  name: "App",
  components: {
    Controller,
    Container,
    MovieItem,
    Spinner,
    ErrHand
  },
  data() {
    return {
      movies: [],
      loading: false,
      err: false,
      currentType: null
    };
  },
  methods: {
    fetchData(type) {
      this.loading = true;
      this.err = false;
      this.currentType = type;
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${type}?api_key=${KEYS.TMDB_KEY}&language=en-US&page=1`
        )
        .then(res => {
          this.movies = res.data.results;
          this.loading = false;
          this.err = false;
        })
        .catch(() => {
          this.loading = false;
          this.err = true;
        });
    }
  },
  mounted() {
    this.fetchData("upcoming");
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.movies-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-auto-rows: auto;
  grid-gap: 10px;
  padding: 25px 0px;
}
</style>
