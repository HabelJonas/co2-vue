<template>
  <header>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
  </header>
  <router-view />
  <footer>
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <h3>Impressum</h3>
          <p>Firmenname GmbH<br>
            Musterstraße 123<br>
            12345 Musterstadt<br>
            Telefon: 0123/456789<br>
            E-Mail: info@firmenname.de</p>
        </div>
        <div class="col-md-6">
          <h3>Rechtliche Hinweise</h3>
          <p>Diese Webseite verwendet Cookies, um Ihnen den bestmöglichen Service zu bieten. Durch die weitere Nutzung der
            Webseite stimmen Sie der Verwendung von Cookies zu. Weitere Informationen finden Sie in unserer
            Datenschutzerklärung.</p>
        </div>
      </div>
    </div>
  </footer>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
