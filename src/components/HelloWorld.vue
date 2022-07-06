<template>
  <div class="hello">
    Xin chào {{ name }}
    <button @click="changeName">Thay đổi</button>
    <hr>
    <div class="mixin">
      <div class="way_1">Quy tắc Mixin (1)</div>
      <div class="way_2">Quy tắc Mixin (2)</div>
    </div>
    <hr>
    <div class="extends">
      Kế thừa (Extends)
    </div>
    <hr>
    <div id="title-import">Import file scss</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      name: "Toàn",
    }
  },
  methods: {
    changeName() {
      this.name = "Đỗ Tiến Toàn"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
/* Biến*/
$whiteColor: blue;

/* Quy tắc mixin*/
/* Cách 1 */
@mixin colorVsFont {
  color: red;
  font-size: 24px;
}

/* Cách 2 */
@mixin colorVsFont_2($color, $fontSize) {
  color: $color;
  font-size: $fontSize;
}

/* Kế thừa (Extends) */
.title {
  color: cadetblue;
  font-size: 40px;
  padding: 30px;
  background: red;
}



.hello {
  button {
    background: $whiteColor;
  }

  .mixin {
    .way_1 {
      @include colorVsFont;
    }

    .way_2 {
      @include colorVsFont_2(blue, 30px)
    }
  }

  .extends {
    @extend .title
  }
}
@import "./src/assets/style/HelloWorld";
</style>
