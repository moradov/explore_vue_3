<template>
  <div class="container">
    <Controller @fetch-data="fetchData" />
  </div>
</template>

<script>
import axios from "axios";
import KEYS from "./assets/keys";
import Controller from "./components/Controller";
export default {
  name: "App",
  components: {
    Controller
  },
  data() {
    return {
      movies: [],
      loading: false,
      err: false
    };
  },
  methods: {
    fetchData(type) {
      this.loading = true;
      this.err = false;
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${type}?api_key=${KEYS.TMDB_KEY}&language=en-US&page=1`
        )
        .then(res => {
          console.log(res);
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
</style>
