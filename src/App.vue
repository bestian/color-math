<template lang="pug">
  #app
    #nav.ui.menu
      router-link.item(to = "/") 倍數著色
      router-link.item(to = "/about") 倍數猜猜看
    router-view
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
  font-size: 20px;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

a {
  cursor: pointer;
}
</style>
