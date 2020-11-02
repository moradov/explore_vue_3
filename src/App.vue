<template>
  <div>hello</div>
</template>

<script>
import axios from "axios";
import KEYS from "./assets/keys";
export default {
  name: "App",
  components: {},

  methods: {
    fetchData() {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/popular?api_key=${KEYS.TMDB_KEY}&language=en-US&page=1`
        )
        .then(res => console.log(res))
        .catch(err => console.log(err));
    }
  },
  mounted() {
    this.fetchData();
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
