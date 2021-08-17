<template>
  <div class="jobDetailContent">
    <div class="jobTitleNCompanyNameDiv">
      <p class="jobTitle">{{ job.title }}</p>
      <p class="companyName">{{ job.companyName }}</p>
      <img
        class="logoCompany"
        v-if="job.urlCompanyLogo"
        :src="job.urlCompanyLogo"
      />
    </div>
    <div class="jobDescriptionDiv">
      <div>
        <JobFeature
          featureName="LUGAR DE TRABAJO"
          :featureValue="job.city + ', ' + job.state"
        ></JobFeature>
        <JobFeature
          featureName="PUBLICADO"
          :featureValue="
            'Publicado el ' + moment(job.createdAt, 'YYYYMMDD').format('LL')
          "
        ></JobFeature>
        <JobFeature
          featureName="SUELDO"
          :featureValue="jobSalary(job.salary)"
        ></JobFeature>
        <JobFeature
          featureName="TIPO DE PUESTO"
          :featureValue="job.jobType"
        ></JobFeature>
        <JobFeature featureName="ÁREA" :featureValue="job.area"></JobFeature>
        <JobFeature
          featureName="MODALIDAD DE TRABAJO"
          :featureValue="job.modality"
        ></JobFeature>
      </div>
      <div class="jobDescription" v-html="job.description"></div>
    </div>
  </div>
</template>

<script>
import JobFeature from "../../components/JobFeature.vue";
import moment from "moment";
export default {
  methods: {
    moment: function(date) {
      return moment(date);
    },
    jobSalary: function(salary) {
      return salary ? salary : "No especificado";
    },
  },
  components: {
    JobFeature,
  },
  async asyncData({ params }) {
    const job = await fetch(
      `https://zonajobsbackend.herokuapp.com/jobAd/${params.idJob}`
    ).then((res) => res.json());
    return { job };
  },
  head() {
    return {
      title: this.job.title,
    };
  },
};
</script>

<style>
:root {
  --paddingRightNLef: 20px;
}
.jobDetailContent {
  width: 100%;
  max-width: 920px;
  margin: 60px auto;
  background: linear-gradient(64deg, #f97072, #ffa164);
}
.jobTitleNCompanyNameDiv {
  padding: 30px var(--paddingRightNLef);
  position: relative;
}
.jobTitle {
  font-size: 18px;
  margin: 0px;
}
.companyName {
  font-size: 16px;
  margin: 10px 0px;
}
.logoCompany {
  display: block;
  width: 100%;
  max-width: 16%;
  min-width: 110px;
  height: auto;
  position: absolute;
  right: var(--paddingRightNLef);
  top: 65px;
  padding: 5px;
  background-color: white;
  border: 1px solid #fe633f;
}
.jobDescriptionDiv {
  background-color: white;
  padding: 20px var(--paddingRightNLef);
  font-size: 15px;
}
.jobDescription {
  border-top: 2px solid #979797;
  padding-top: 20px;
  margin-top: 20px;
}
.loadingAnimationContainer {
  width: 150px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.loadingAnimation {
  border: 12px solid #fb9077;
  border-radius: 50%;
  border-top: 12px solid #5e61ca;
  width: 60px;
  height: 60px;
  animation: rotate 2s linear infinite;
}
@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

@media (max-width: 556px) {
  .logoCompany {
    top: 100px;
  }
}
</style>
