<template lang="pug">
  .hello
    h1 倍數著色
    hr
    br
    h3
      span(v-if = "myNum == 1000") 點擊任意數字，自動畫出它的所有倍數 
      span(v-if = "myNum !== 1000") {{myNum}}的倍數
    br
    .ui.grid.container
      .ui.ten.column.row(v-for = "i in [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]")
        .ui.column(v-for = "j in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]")
          a(@click = "makeColor(i+j)" v-bind:class = "{ 'color' : (i+j) % myNum == 0}") {{i + j}}
    br
    hr
    h3
      span(v-if = "myNum !== 1000") 想想看，為什麼{{myNum}}的倍數會形成這樣的圖樣呢?
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      myNum : 1000
    }
  },
  methods: {
    makeColor (n) {
      this.myNum = n;
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

.color {
  background-color: #af0;
}
</style>
