<template>
  <div class="btn-group mb-5" role="group">
    <button
      v-for="item in controlsList"
      :key="item.id"
      type="botton"
      :class="item.id === current ? 'btn btn-primary active' : 'btn btn-primary' "
      @click="controlChangeHand(item.id) "
    >{{item.name}}</button>
  </div>
</template>
<script>
export default {
  name: "Controller",
  props: ["fetch-data"],
  data() {
    return {
      controlsList: [
        { id: "upcoming", name: "Upcoming" },
        { id: "popular", name: "Pouplar" },
        { id: "top_rated", name: "Top Rated" }
      ],
      current: "upcoming"
    };
  },
  methods: {
    controlChangeHand(item) {
      this.current = item;
    }
  },
  watch: {
    current(newState) {
      this.$emit("fetch-data", newState);
    }
  }
};
</script>