<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
    <menu></menu>
     分割线
    <foot msgFromFather='来自父组件的消息' v-on:child-tell-me-something='listenToMyBoy'></foot>
    <div> {{ money | formartMoney}}</div>
  </div>
</template>

<script>
import Menu from './components/menu'
import Foot from './components/foot'

export default {
  name: 'app',
  created(){

  },
  data () {
    return{
        money: 100
      }
  },
  components: { // 注册组件才能使用,SelectItem Vue会把这个转化成 <select-item></select-item>
    Menu, 
    Foot
  },
  methods:{
    listenToMyBoy:function(msg){
      alert(msg)
    }
  },
  filters:{
    formartMoney:function (value){
      return "￥ " + value
    }
  },
  events:{
    'child-tell-me-something-dispatch' : function(msg){
      alert(msg)
    }
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
