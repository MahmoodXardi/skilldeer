<template>
  <div id="app">
    <nav class="navbar is-primary" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item">
          <img src="https://static.skilldeer.com/prod/images/logo.png" width="112" height="30">
        </router-link>
      </div>

        <div class="navbar-menu ">
        <!-- navbar start, navbar end -->
          <div class="navbar-start">
          <!-- navbar items -->
            <router-link to="/explore" class="navbar-item">Explore classes</router-link>
          </div>
        </div>
    </nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

</style>
