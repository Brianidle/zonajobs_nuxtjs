<template>
  <div class="navForFilteringContent">
    <FilteringGroup :filterGroupName="filterGroupName"/>
    <FilteringGroup :filterGroupName="filterGroupName"/>
    <FilteringGroup :filterGroupName="filterGroupName"/>
  </div>
</template>

<script>
import FilteringGroup from "../components/FilteringGroup.vue";
export default {
  props:{
    filterGroupName:String
  },
  components: {
    FilteringGroup,
  },
};
</script>

<style>
.navForFilteringContent {
  background-color: white;
  padding: 0px 10px;
  flex-shrink: 0;
  height: 100%;
}

@media (max-width: 700px) {
  .navForFilteringContent {
    display: none;
  }
}
</style>
