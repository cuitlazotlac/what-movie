<template>
  <header className="header">
    <router-link to="/">
      <!-- <img src="./assets/img/main_img.png" /> -->
      <a>
        <img className="icon" src="./assets/img/github.png" />
      </a>
      <a>What Movie ?</a>
      <a>
        <img className="github" src="./assets/img/github.png" />
      </a>
    </router-link>
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
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #181829;
  box-shadow: 0 0 6 rgba(0, 0, 0, 0.1);
  @media only screen and (max-width: 600px) {
    .icon {
      width: 6%;
    }
    .github {
      width: 6%;
    }
  }
}

h1 {
  color: #f6c46a;
  font-size: 28px;
}

.header {
  a {
    color: #f6c46a;
    font-size: 22px;
    font-weight: 900;
  }
}

.icon {
  width: 3%;
  position: absolute;
  right: 0px;
  width: 300px;
  float: left;
}
.github {
  width: 3%;
  margin-right: 5px;
}
</style>
