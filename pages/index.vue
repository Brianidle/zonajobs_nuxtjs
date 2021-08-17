<template>
  <div>
    <div class="searchSectionImageBackground">
      <div class="searchSection">
        <div class="searchSectionMessage">Empleá tu pasión</div>
        <SearchBar />
      </div>
    </div>
    <div class="jobSection">
      <div class="jobSectionHeader">
        <label class="countryLabel">Argentina</label>
        <label class="allCountryAdsLabel">VER AVISOS DE TODO ARGENTINA</label>
      </div>
      <div class="jobSectionContent">
        <NavForFiltering filterGroupName="Dia de entrega" />
        <div class="jobAdsSection">
          <label class="featuredJobsTitle">
            Empleos destacados en <strong>Argentina</strong>
          </label>
          <JobAds :jobAds="jobAds" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "../components/SearchBar.vue";
import NavForFiltering from "../components/NavForFiltering.vue";
import JobAds from "../components/JobAds.vue";
export default {
  data() {
    return {
      jobAds: [],
    };
  },
  async fetch() {
    this.jobAds = await fetch(
      "https://zonajobsbackend.herokuapp.com/jobAd/all"
    ).then((res) => res.json());
  },
  components: {
    SearchBar,
    NavForFiltering,
    JobAds,
  },
};
</script>

<style>
.searchSectionImageBackground {
  background-image: url(https://imgzj.jobscdn.com/postulantes-assets/skins/zonajobs/postulantes-desktop/img/zj_portada_site.jpg);
  background-size: cover;
  height: 235px;
  margin-bottom: 15px;
}

.searchSectionMessage {
  font-size: 22px;
  color: #fff;
  font-weight: 300;
  padding-bottom: 10px;
}

.searchSection {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 1170px;
  height: 235px;
  margin: 0px auto;
}

.jobSection {
  width: 1170px;
  margin: 0px auto;
  background-color: #f5f5f5;
}

.jobSectionHeader {
  display: flex;
  flex-direction: row;
  align-items: center;
  background-color: #fff;
  padding: 15px 15px;
  margin-bottom: 15px;
}

.countryLabel {
  font-size: 14px;
  color: #000;
}

.allCountryAdsLabel {
  float: right;
  margin-left: auto;
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
  color: #585992;
}

.jobSectionContent {
  display: flex;
  flex-direction: row;
}

.featuredJobsTitle {
  display: inline-block;
  font-size: 24px;
  margin-bottom: 15px;
}

.jobAdsSection {
  margin-left: 15px;
  margin-bottom: 40px;
}

@media (max-width: 615px) {
  .allCountryAdsLabel {
    width: 150px;
    text-align: center;
  }
}

@media (max-width: 700px) {
  .jobAdsSection {
    width: 100%;
    margin-left: unset;
  }
}

@media (max-width: 1250px) {
  .searchSection {
    width: 95%;
  }

  .jobSection {
    width: 95%;
  }
}
</style>
