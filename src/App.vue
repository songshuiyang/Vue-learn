<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
    <menu></menu>
     分割线
    <foot msgFromFather='来自父组件的消息' v-on:child-tell-me-something='listenToMyBoy'></foot>
    <div> {{ money | formartMoney}}</div> 
    <!-- 模板语法来声明式的将数据渲染进 DOM 的系统 -->
    <span v-bind:title="message">
        鼠标悬停几秒钟查看此处动态绑定的提示信息！
    </span>
    <span>
      {{reversedMessage}}
    </span>
    <div>
      <ol>
        <li v-for="todo in tools" :key="todo.text">
            {{todo.text}}
        </li>
      </ol>
    </div>
    <!-- v-bind 缩写：
         v-on 缩写 @  -->
    <div v-bind:class="classObject">classObject</div>
 
    <input type="button" v-on:click="toggle()" value="v-show"/>
    <div v-show="isShow" style="width: 100px;height: 100px;background: red"></div>
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
        money: 100 ,
        message: 'helloWorld',
        tools: [
          {text: 'Java'},
          {text: 'C++'},
          {text: 'C#'}
        ],
        classObject:{
          active: true,
          'text-danger': false
        },
        isShow:false
      }
  },
  components: { // 注册组件才能使用,SelectItem Vue会把这个转化成 <select-item></select-item>
    Menu, 
    Foot
  },
  methods:{
    listenToMyBoy:function(msg){
      alert(msg)
    },
    toggle:function(){
      this.isShow = !this.isShow
    }
  },
  computed:{
  // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
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
