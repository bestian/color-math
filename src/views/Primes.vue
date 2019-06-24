<template lang="pug">
  .hello
    h1 質數篩法
    a.ui.huge.green.button(@click = "start()") 開始!
    hr
    h4 第{{step}}步
    br
    .ui.grid.container
      .ui.ten.column.row(v-for = "i in [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]")
        .ui.column(v-for = "j in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]")
          a(@click = "makeColor(i+j)" v-bind:class = "{ 'color' : (i+j) % myNum == 0, 'color1' : i+j == 1, 'color2' : (i+j) % 2 == 0 && i+j != 2 && step > 0, 'color3' : (i+j) % 3 == 0 && i+j != 3 && step > 1, 'color5' : (i+j) % 5 == 0 && i+j != 5 && step > 2, 'color7' : (i+j) % 7 == 0 && i+j != 7 && step > 3}") {{ i+j }}
    br
    hr
    .ui.segment.container
      h3(v-if = "step != 5") {{primes.slice(0,step)}}   
      h3(v-if = "step == 5") {{primes}}   
</template>

<script>
export default {
  name: 'Primes',
  data () {
    return {
      myNum : 1000,
      step : 0,
      primes : [2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,77,79,83,89,97]
    }
  },
  methods: {
    makeColor (n) {
      this.myNum = n;
    },
    go() {
      this.step++;
      this.step = this.step % 6;
    },
    start() {
      setInterval(this.go, 2000)
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
  color: #39c;
  font-size: 20px;
  display: inline-block;
  min-width: 6vw !important;
  width: 100%;
  padding: 3px 2px;
  border: 1px black solid;
}
a.color {
  background-color: #af0 !important;
}

a.color1 {
  background-color: #999;
}

a.color2 {
  background-color: #c03;
}

a.color3 {
  background-color: #f00;
}

a.color5 {
  background-color: #c30;
}

a.color7 {
  background-color: #a00;
}
</style>

