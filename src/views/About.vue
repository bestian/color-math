<template lang="pug">
  .hello
    h1(v-if = "!isWin && !isLoose") 圖樣猜猜看
    h1(v-if = "isLoose") 不對喔，再試試看吧
    h1(v-if = "isWin") 你猜對了!!是{{myNum}}的倍數
    br
    .ui.huge.green.button(@click = "reset()") 猜猜看!
    hr
    br
    .ui.grid.container
      .ui.ten.column.row(v-for = "i in [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]")
        .ui.column(v-for = "j in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]")
          a(v-bind:class = "{ 'color' : (i+j) % myNum == 0}") ?
    br
    hr
    h3
      span(v-if = "myNum !== 1000") 猜猜看，這是誰的倍數，會形成這樣的圖樣呢?
    .ui.icon.input
      input(type = "number" min = "1" max = "10" step="1" v-model="gNum" @change="guessNum(gNum)")
      i.search.icon
</template>


<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      myNum : 1000,
      gNum : 1,
      isWin: false,
      isLoose: false
    }
  },
  methods: {
    reset () {
      this.myNum = Math.floor(Math.random()*8 + 2);
      this.isWin = false;
      this.isLoose = false;
    },
    guessNum (n) {
      if (this.myNum == n) {
        this.win()
      } else {
        this.isLoose = true;
        this.isWin = false;
      }
    },
    win() {
      this.isWin = true;
      this.isLoose = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ui.row {
  padding: 0 !important;
}
.ui.column {
  text-align: right;
}

a {
  color: #42b983;
  font-size: 20px;
  display: inline-block;
  min-width: 6vw !important;
  padding: 3px 0;
  border-radius: 3px;
}
.color {
  background-color: #cf3;
}
</style>

