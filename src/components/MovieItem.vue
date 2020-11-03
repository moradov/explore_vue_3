<template>
  <div class="card" style="width : 18rem">
    <img
      class="card-img-top"
      :alt="`${name} poster `"
      :src="`https://image.tmdb.org/t/p/w500${img_src} `"
      style="height : 400px"
    />
    <div class="card-body">
      <h5 class="card-titme">{{name}}</h5>
      <p class="card-text">{{overview.substring(0, 100) + "..." }}</p>
      <a href="#" class="btn btn-primary">View More</a>
    </div>
  </div>
</template>
<script>
export default {
  name: "MovieItem",
  props: ["name", "img_src", "overview"]
};
</script>