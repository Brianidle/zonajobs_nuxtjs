<template>
  <header>
    <div class="navContainer">
      <div class="navigationBar">
        <a class="pageLogoButton" href="/">
          <img
            class="pageLogo"
            src="https://imgzj.jobscdn.com/postulantes-assets/skins/zonajobs/commons/img/logo-zonajobs.svg"
          />
        </a>

        <div class="navButtons">
          <div class="optionButtonsContainer">
            <a class="optionButton ">Posiciones Ejecutivas</a>
            <a class="optionButton">Blog de Noticias</a>
            <a class="optionButton">Soy Empresa</a>
          </div>
          <div class="specialButtonsContainer">
            <a class="navBarPublishButton" href="/empresas/formularioGratis"
              >Publicar Gratis</a
            >
            <a class="navBarLogInButton">Ingresar</a>
          </div>
        </div>

        <div class="navBarSeparator"></div>

        <button class="dropdownButton">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="#000000"
            viewBox="0 0 16 16"
          >
            <path
              fillRule="evenodd"
              d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"
            />
          </svg>
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {};
</script>

<style scoped>
header {
  z-index: 2;
  position: fixed;
  top: 0px;
  width: 100%;
  background-color: white;
}

.navContainer {
  height: 58px;
  width: 1170px;
  margin: 0px auto;

  font-family: "Open Sans", sans-serif;
  font-size: 14px;
  font-weight: 600;
}

.navigationBar {
  display: inline-flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
  height: 100%;
}

.pageLogoButton {
  flex-shrink: 0;
}

.pageLogo {
  width: 90px;
}

.navButtons {
  display: inline-flex;
  flex-direction: row;
  margin-left: auto;
  align-items: center;
  font-size: 14px;
  text-transform: uppercase;
  font-weight: 400;
}

.optionButtonsContainer {
  margin-right: 15px;
}

.navBarSeparator {
  display: none;
  width: 10px;
}

.dropDownContainer {
  position: absolute;
  background-color: white;
  top: 50px;
  right: 30px;
}

.dropdownButton {
  display: none;
  height: 40px;
  width: 40px;
  flex-shrink: 0;
  background-color: transparent;
  border: unset;
  padding: 0px;
}

.dropdownButton:hover {
  cursor: pointer;
}

.optionButton {
  color: #585992;
  padding: 10px 5px;
  margin-right: 15px;
  border-radius: 20px;
  transition-duration: 250ms;
}

.optionButton:hover {
  background-color: #ada8a83a;
}

.navBarButton {
  margin-right: 15px;
  border-radius: 20px;
}

.navBarButton:last-child {
  margin-right: 0px;
}

.navBarOptionButton {
  padding: 10px 5px;
}

.navBarPublishButton {
  border: 1px solid #585992;
  padding: 10px 20px;
  border-radius: 20px;
  color: #585992;
  transition-duration: 250ms;
}

.navBarPublishButton:hover {
  background-color: #585992;
  color: white;
}

.navBarLogInButton {
  border: 1px solid #fe633f;
  padding: 10px 20px;
  border-radius: 20px;
  color: #fe633f;
  transition-duration: 250ms;
}

.navBarLogInButton:hover {
  background-color: #fe633f;
  color: white;
}

@media (max-width: 545px) {
  .specialButtonsContainer {
    display: none;
  }
}

@media (max-width: 1010px) {
  .optionButtonsContainer {
    display: none;
  }
  .dropdownButton {
    display: block;
  }

  .navBarSeparator {
    display: block;
  }
}

@media (max-width: 1250px) {
  .navContainer {
    width: 95%;
  }
}
</style>
