<template>
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--    <NewComponent></NewComponent>-->
<!--    <KienThucB1></KienThucB1>-->
<!--    <KienThucB2></KienThucB2>-->
<!--    <BaiTap3></BaiTap3>-->
    <BT2Buoi2></BT2Buoi2>
  </div>
</template>

<script>
/*import HelloWorld from './components/HelloWorld.vue'*/
// import NewComponent from './components/NewComponent'
// import KienThucB1 from './components/HocNhom/KienThucB1'
// import KienThucB2 from './components/HocNhom/KienThucB2'
// import BaiTap3 from './components/BaiTap3'
import BT2Buoi2 from './components/HocNhom/BT2Buoi2'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    // NewComponent,
    // KienThucB1,
    // KienThucB2,
    // BaiTap3
    BT2Buoi2
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
