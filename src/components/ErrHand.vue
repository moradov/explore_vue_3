<template>
  <div class="card" style="width : 18rem; border :none; margin-top :150px">
    <div class="card-body text-center">
      <h5 class="card-text">Error</h5>
      <p class="card-text">Something Went Wrong</p>
      <button class="btn btn-secondary" @click="tryAgainHand ">
        <span class="glyphicon glyphicon-refresh" aria-hidden="trua">Try Again</span>
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "ErrHand",
  props: ["loadAgain"],
  methods: {
    tryAgainHand() {
      this.loadAgain();
    }
  }
};
</script>