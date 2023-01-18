<template>
  <nav>
    <router-link to="/">
      <h1><span>Vue</span>Movies</h1>
    </router-link>
  </nav>
  <main>
    <router-view/>
  </main>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}

nav {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 15px;
}

span {
  color: blueviolet;
}

</style>
