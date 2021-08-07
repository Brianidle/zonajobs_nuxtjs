<template>
  <div>
    <NavBar />
    <nuxt class="pagesTemplate" />
  </div>
</template>

<script>
import NavBar from "../components/NavBar";

export default {
  components: {
    NavBar,
  },
};
</script>

<style>
.pagesTemplate {
  background-color: #f5f5f5;
  padding-top: 58px;
}
</style>
