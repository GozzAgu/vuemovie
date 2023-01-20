<template>
  <nav>
    <router-link class="link" to="/">
      <h1><b>Vue </b><span class="badge bg-secondary">Movies</span></h1>
    </router-link>
  </nav>
  <main>
    <router-view/>
  </main>
</template>

<script setup>

</script>

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

.link {
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
