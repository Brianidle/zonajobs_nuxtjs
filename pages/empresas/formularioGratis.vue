<template>
  <div class="publishJobAdDiv">
    <div class="publishJobAdContent">
      <header class="header_1">
        <h1 class="publishAFreeAdTitle">PUBLICÁ UN AVISO GRATIS</h1>
        <span class="freeAdsAvailable">Tenés 3 avisos gratis disponibles</span>
      </header>
      <form class="formContainer" @submit="onSubmit">
        <div style="margin-bottom: 20px; position: relative;">
          <label class="inputDescription">
            Puesto / Título del aviso
          </label>
          <input
            v-model="title"
            type="text"
            :maxlength="maxNumberOfCharactersTitle"
            required
          />
          <label class="numberOfWords"
            >{{ title.length }}/{{ maxNumberOfCharactersTitle }}</label
          >
        </div>
        <div style="margin-bottom:20px;">
          <label class="inputDescription">
            Descripción del puesto
          </label>
          <CKEditor5
            :onChangeDataEditor="onChangeDataEditor"
            :maxNumberOfCharacters="maxNumberOfCharactersDescription"
          />
        </div>
        <div class="inputsGrid">
          <div>
            <label class="inputDescription">Área de empleo</label>
            <input v-model="area" required />
          </div>
          <div>
            <label class="inputDescription">
              Subárea de empleo
            </label>
            <div>
              <input v-model="subArea" required />
            </div>
          </div>
          <div>
            <label class="inputDescription">País</label>
            <input v-model="country" disabled />
          </div>
          <div>
            <label class="inputDescription">Provincia</label>
            <input v-model="state" required />
          </div>
          <div>
            <label class="inputDescription">Ciudad</label>
            <input v-model="city" required />
          </div>
          <div>
            <label class="inputDescription">Dirección</label>
            <input v-model="address" required />
          </div>
          <div>
            <label class="inputDescription">Sueldo</label>
            <input v-model="salary" :disabled="salaryInputDisable" required />
            <input
              type="checkbox"
              @click="onClickCheckBox"
              style="margin: 10px 5px 0px 0px"
            /><label>No especificado</label>
          </div>
          <div>
            <label class="inputDescription">
              Tipo de Empleo
            </label>
            <input v-model="jobType" required />
          </div>
          <div>
            <label class="inputDescription">
              Modalidad de Trabajo
            </label>
            <input v-model="modality" required />
          </div>
          <div>
            <label class="inputDescription">
              Nombre de la Empresa
            </label>
            <input v-model="companyName" required />
          </div>
          <div>
            <label class="inputDescription">
              Url del Logo de la Empresa
            </label>
            <input v-model="urlCompanyLogo" />
          </div>
        </div>
        <div style="text-align: center;">
          <button class="publishButton" type="submit">PUBLICAR</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import CKEditor5 from "../../components/CKEditor5.vue";
const maxNumberOfCharactersDescription = 3500;
const maxNumberOfCharactersTitle = 100;

export default {
  data() {
    return {
      title: "",
      description: "",
      area: "",
      subArea: "",
      country: "Argentina",
      state: "",
      city: "",
      address: "",
      salary: "",
      jobType: "",
      modality: "",
      companyName: "",
      urlCompanyLogo: "",
      salaryInputDisable: false,
      maxNumberOfCharactersDescription,
      maxNumberOfCharactersTitle,
    };
  },
  methods: {
    onSubmit: function(e) {
      e.preventDefault();

      fetch("https://zonajobsbackend.herokuapp.com/jobAd", {
        method: "post",
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          title: this.title,
          description: this.description,
          area: this.area,
          subArea: this.subArea,
          country: this.country,
          state: this.state,
          city: this.city,
          address: this.address,
          salary: this.salary,
          jobType: this.jobType,
          modality: this.modality,
          companyName: this.companyName,
          urlCompanyLogo: this.urlCompanyLogo,
        }),
      });

      this.$router.replace("/");
    },
    onClickCheckBox: function() {
      this.salary = "";
      this.salaryInputDisable = !this.salaryInputDisable;
    },
    onChangeDataEditor: function(dataEditor) {
      this.description = dataEditor;
    },
    verifyInput: function() {
      return (
        this.title.length <= maxNumberOfCharactersTitle &&
        numberOfCharactersDescription <= maxNumberOfCharactersDescription
      );
    },
  },
  components: {
    CKEditor5,
  },
};
</script>

<style>
.header_1 {
  text-align: center;
}
.publishJobAdDiv {
  width: 100%;
  max-width: 920px;
  margin: 40px auto;
  background-color: white;
}
.publishJobAdContent {
  padding: 35px 20px;
}
.publishAFreeAdTitle {
  font-weight: 700;
  line-height: 30px;
  font-size: 22px;
  color: #535151;
  margin: 0px;
}
.numberOfWords {
  position: absolute;
  bottom: 5px;
  right: 10px;
  font-size: 14px;
}
.freeAdsAvailable {
  font-size: 14px;
  color: #212121;
}
.formContainer {
  margin-top: 20px;
}
.inputDescription {
  display: inline-block;
  font-size: 16px;
  margin-bottom: 5px;
}
input:not(input[type="checkbox"]) {
  box-sizing: border-box;
  width: 100%;
  padding: 0 10px;
  border-radius: 3px;
  border: 1px solid #e5e5e5;
  height: 35px;
  font-size: 14px;
}
input:hover {
  box-shadow: inset 0 0 5px #66afe9;
}
.inputsGrid {
  display: grid;
  grid-template-columns: calc(50% - 10px) calc(50% - 10px);
  grid-column-gap: 20px;
  grid-row-gap: 20px;
}
.publishButton {
  width: 100%;
  max-width: 220px;
  color: #fff;
  background-color: #ff652b;
  box-shadow: 0 2px 4px 0 rgb(0 0 0 / 50%);
  border: none;
  cursor: pointer;
  font-family: "Open Sans", sans-serif;
  margin-bottom: 0;
  font-weight: 600;
  padding: 10px 25px;
  font-size: 14px;
  text-transform: uppercase;
  border-radius: 2px;
  margin-top: 30px;
}
@media (max-width: 767px) {
  .inputsGrid {
    grid-template-columns: 100%;
    grid-column-gap: unset;
  }
}
</style>
