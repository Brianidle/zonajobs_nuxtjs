<template>
  <li>
    <a class="filterName">{{ filterName }}</a>
    <span v-if="numberOfMatches" class="numberOfMatches">({{
      numberOfMatches
    }})</span>
  </li>
</template>

<script>
export default {
  props: ["filterName", "numberOfMatches"],
};
</script>

<style>
.filterName {
  font-size: 14px;
  display: inline-block;
  color: #585992;
  width: 80%;
  overflow: hidden;
  text-overflow: ellipsis;
}

.numberOfMatches {
  font-size: 14px;
  color: #8c8c8c;
  float: right;
}
</style>
