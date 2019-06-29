<template lang="pug">
  #app
    #nav.inverted.icon.labeled.ui.menu
      router-link.item(to = "/")
        i.certificate.icon
        | 倍數著色
      router-link.item(to = "/about")
        i.question.icon
        | 猜猜看
      router-link.item(to = "/primes")
        i.law.icon
        | 質數篩法
    router-view
</template>

<style>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #FFFF99;
  height: 100vh;
}

a.item {
  font-size: 1.4em !important;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

a {
  cursor: pointer;
  font-weight: bold;
}
</style>
