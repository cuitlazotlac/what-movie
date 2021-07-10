<template>
  <header>
    <router-link to="/">
      <!-- <img src="./assets/img/main_img.png" /> -->
      <h1><span>Vue</span>movies</h1>
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

  &::selection {
    background: transparentize($color: #42b883, $amount: 0.5);
  }
}

body {
  background-color: #f0f3f5;
}

a {
  text-decoration: none;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2c3d4e;
  box-shadow: 0 0 6 rgba(0, 0, 0, 0.1);
}

h1 {
  color: #fff;
  font-size: 28px;

  span {
    color: #42b883;
  }
}
</style>
