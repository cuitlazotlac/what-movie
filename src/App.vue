<template>
  <header className="header">
    <!-- <router-link to="/"> -->
    <!-- <img src="./assets/img/main_img.png" /> -->
    <a href="/">
      <img className="icon" src="./assets/img/logo.png" />
    </a>
    <a className="app_title" href="/">What Movie ?</a>
    <a href="https://github.com/cuitlazotlac/what-movie" target="_blank">
      <img className="github" src="./assets/img/github.png" />
    </a>
    <!-- </router-link> -->
  </header>
  <main>
    <router-view />
  </main>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  // font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-family: "Inter", sans-serif;

  // &::selection {
  //   background: transparentize($color: #42b883, $amount: 0.5);
  // }
}

body {
  background-color: #f7f9fa;
}

a {
  text-decoration: none;
}

header {
  // display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #f7f9fa;
  border-bottom: 0.5px solid rgba(138, 138, 138, 0.24);
  box-shadow: 0px -17px 27px -5px #000000;
  .app_title {
    color: #f6c46a;
    font-size: 22px;
    font-weight: 900;
    align-items: left;
  }
  .icon {
    width: 2%;
    float: left;
    margin-right: 15px;
  }
  .github {
    width: 2%;
    float: right;
    margin-right: 5px;
  }

  @media only screen and (max-width: 600px) {
    .app_title {
      font-size: 16px;
    }
    .icon {
      width: 8%;
    }
    .github {
      width: 8%;
    }
  }
}
</style>
