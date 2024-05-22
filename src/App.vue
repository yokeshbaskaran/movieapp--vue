<template>
  <header>
    <RouterLink to="/">
      <h1><span>Vue</span>Movies</h1>
    </RouterLink>
  </header>

  <main>
    <router-view />
  </main>

  <footer>CopyRights &copy; 2024</footer>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
  &::selection {
    background: transparentize($color: #428883, $amount: 0.5);
  }
  text-decoration: none;
}

body {
  background-color: #35495e;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2c3d4e;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #fff;
  font-size: 28px;

  span {
    color: #42b883;
  }
}

footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  padding: 8px;
  color: white;
  background-color: #2c3d4e;
}
</style>
