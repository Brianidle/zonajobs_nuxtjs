<template>
  <div class="jobFeatureContainer">
    <p class="featureName">{{ featureName }}</p>
    <p class="featureValue">{{ featureValue }}</p>
  </div>
</template>

<script>
export default {
  props: {
    featureName: String,
    featureValue: String,
  },
};
</script>

<style>
.jobFeatureContainer {
  display: inline-block;
  width: 100%;
  max-width: 250px;
}
.featureName {
  font-size: 12px;
  color: #8c8c8c;
  font-weight: 400;
  text-transform: uppercase;
  text-align: left;
  line-height: normal;
}
.featureValue {
  margin: 0px;
  font-size: 13px;
  font-weight: 400;
}
</style>
