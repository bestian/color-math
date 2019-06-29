<template lang="pug">
  .hello
    h3
      span(v-if = "myNum !== 1000 && !isWin") 猜猜看，這是誰的倍數，會形成這樣的圖樣呢?
    .ui.icon.input(v-if = "myNum !== 1000 && !isWin")
      input(type = "number" min = "1" max = "10" step="1" v-model="gNum" @change="guessNum(gNum)")
      i.search.icon
    h1(v-if = "isLoose") 不對喔，再試試看吧
    h1(v-if = "isWin") 你猜對了!!是{{myNum}}的倍數
    hr
    br
    .ui.huge.green.button(v-if = "step == 0", @click = "reset()") 猜猜看!
    br
    br
    .ui.grid.container
      .ui.ten.column.row(v-for = "i in [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]")
        .ui.column(v-for = "j in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]")
          a(v-bind:class = "{ 'color' : (i+j) % myNum == 0, 'small': i+j == 100}") ?

</template>


<script>
export default {
  name: 'Guess',
  data () {
    return {
      myNum: 1000,
      gNum: 1,
      step: 0,
      isWin: false,
      isLoose: false
    }
  },
  methods: {
    reset () {
      this.myNum = Math.floor(Math.random()*8 + 2);
      this.isWin = false;
      this.isLoose = false;
      this.step = 1;
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
      this.isLoose = false;
      this.step = 0;
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
  padding: 0 !important;
  overflow: hidden;
}

a {
  color: #99f;
  text-align: center;
  font-size: 22px;
  display: inline-block;
  min-width: 6vw !important;
  width: 100%;
  padding: 6px 2px;
  border: 1px black solid;
}


.color {
  background-color: #cf3;
}

</style>

