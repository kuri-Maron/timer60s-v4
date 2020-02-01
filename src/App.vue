<template>
  <div id="app">
    <div class="container">
      <b-button variant="success">Button</b-button>
      <div id="nav">
        <router-link to="/">Home</router-link>|
        <router-link to="/about">About</router-link>
      </div>
      <router-view />
    </div>
  </div>
</template>

<script>
// アイコン使いたいならインポートが必要？
// import { BootstrapVue, BootstrapVueIcons } from 'bootstrap-vue'
// Vue.use(BootstrapVueIcons)

export default {
  name: "App"
}
</script>

<style>

html {
  background-color: #444;
}

#app {
  /* デフォルト設定 */
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

/* カスタム設定 */
  /* background-color: rgb(56, 51, 51); */
  background-color: #444;
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
