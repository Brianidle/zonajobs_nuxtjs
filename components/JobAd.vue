<template>
  <a class="jobAdContent" :href="'/empleos/' + job._id">
    <p class="publishedAgoSpan">
      publicado el {{ moment(job.createdAt, "YYYYMMDD").format("LL") }}
    </p>
    <div class="jobDescriptionContent">
      <img
        v-if="job.urlCompanyLogo"
        class="jobCompanyLogoImage"
        :src="job.urlCompanyLogo"
      />
      <div class="jobTitle">{{ job.title }}</div>
      <div class="companyName">{{ job.companyName }}</div>
      <div class="jobLocation">
        <label>{{ job.city }}</label
        >, <label>{{ job.state }}</label>
      </div>
      <p class="jobDescription">
        {{ removeHTMLTags(job.description) + " ..." }}
      </p>
    </div>
  </a>
</template>

<script>
import moment from "moment";
export default {
  props: ["jobAd"],
  data() {
    return {
      job: this.jobAd,
    };
  },
  methods: {
    moment: function(date) {
      return moment(date);
    },
    removeHTMLTags: function(htmlString) {
      return htmlString.replace(/(<([^>]+)>)/gi, "");
    },
  },
};
</script>

<style>
.publishedAgoSpan {
  text-transform: uppercase;
  float: right;
  font-size: 12px;
  margin-top: 8px;
  margin-bottom: 5px;
  margin-right: 15px;
}

.jobDescriptionContent {
  border-top: 1px solid rgba(186, 187, 202, 0.5);
  margin: 0px 15px;
  padding: 15px 0px;
  clear: both;
}

.jobCompanyLogoImage {
  width: 90px;
  height: 57px;
  float: right;
  padding-left: 10px;
}

.jobTitle {
  display: block;
  margin: 0px;
  margin-bottom: 10px;
  color: #3a3a3a;
  font-size: 14px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.companyName {
  display: block;
  margin-bottom: 5px;
  font-size: 13px;
  font-weight: 600;
  color: #3a3a3a;
}

.jobLocation {
  margin: 0px;
  margin-bottom: 10px;
  font-size: 12px;
}
.jobLocation:before {
  content: "\26CA";
  padding-right: 5px;
}

.jobDescription {
  overflow: hidden;
  margin: 0px;
  margin-bottom: 10px;
  max-height: 50px;
  font-size: 14px;
}

.jobAdContent {
  box-sizing: border-box;
  width: 100%;
  background-color: #fff;
  color: gray;
  border: 1px solid rgba(144, 144, 144, 0.5);
  min-width: 0px;

  transition-duration: 150ms;
}

.jobAdContent:hover {
  box-shadow: 0 0 4px 4px rgb(255 161 100 / 60%);
}
</style>
