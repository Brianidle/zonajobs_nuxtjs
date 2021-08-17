<template>
  <div class="jobAdsContent">
    <JobAd v-for="jobAd in jobAds" :key="jobAd._id" :jobAd="jobAd" />
  </div>
</template>

<script>
import JobAd from "../components/JobAd.vue";
export default {
  props: ["jobAds"],
  data() {
    return {
      jobs: this.jobAds,
    };
  },
  components: {
    JobAd,
  },
};
</script>

<style>
.jobAdsContent {
  display: grid;
  grid-template-columns: calc(50% - 5px) calc(50% - 5px);
  grid-column-gap: 10px;
  grid-row-gap: 10px;
}
@media (max-width: 1100px) {
  .jobAdsContent {
    grid-template-columns: 100%;
  }
}
</style>
