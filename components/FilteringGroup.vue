<template>
  <div class="filteringGroupContent">
    <span class="filterGroupName">{{ filterGroupName }}</span>
    <ul class="filteringRowList">
      <FilteringRow filterName="Ayer" numberOfMatches="5" />
      <FilteringRow filterName="Hoy" numberOfMatches="10" />
      <FilteringRow filterName="Mañana" numberOfMatches="15" />
      <FilteringRow filterName="La otra semana" numberOfMatches="20" />
      <FilteringRow filterName="El otro mes" />
      <FilteringRow filterName="El otro año" />
    </ul>
  </div>
</template>

<script>
import FilteringRow from "../components/FilteringRow.vue";
export default {
  props: {
    filterGroupName: String,
  },
  components: {
    FilteringRow,
  },
};
</script>

<style>
.filterGroupName {
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
}

.filteringRowList {
  padding: 0px;
}

.filteringGroupContent {
  width: 210px;
  border-top: 2px solid #dbdbdb;
  padding-top: 10px;
}

.filteringGroupContent:first-child {
  border-top: unset;
}
</style>
