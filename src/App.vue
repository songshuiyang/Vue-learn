<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <router-view/>
    <menu></menu>
    <foot></foot>
  </div>
</template>

<script>
import Menu from './components/menu'
import Foot from './components/foot'

export default {
  name: 'app',
  components: { // 注册组件才能使用,SelectItem Vue会把这个转化成 <select-item></select-item>
    Menu, 
    Foot
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
