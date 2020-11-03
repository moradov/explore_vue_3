<template>
  <div class="center-flex">
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: "Center"
};
</script>
<style>
.center-flex {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>