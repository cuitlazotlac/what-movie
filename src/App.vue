<template>
<header>
    <router-link to="/">
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
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;

  &::selection{
    background: transparentize($color: #42B883, $amount: 0.5);
  }
  }

  body {
    background-color: #35495E;
  }

  a {
    text-decoration: none;
  }

  header{
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 10px 16px;
      background-color: #2C3D4E;
      box-shadow: 0 0 6 rgba(0, 0, 0, 0.1);
  }

  h1{
    color: #FFF;
    font-size: 28px;

    span{
      color: #42B883;
      }
    }
</style>
