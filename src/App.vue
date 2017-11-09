<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
    <!-- 如果出现Do not use built-in or reserved HTML elements as component id警告处理方式
这样的报错原因是因为在App.vue父组件里有<component></component>标签，有重名了。所以要把原来的标签名换掉，例:<componentHello>。这里尽量不要设置为component。 -->
    <menu1>
      <div>ffff</div>
    </menu1>
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


   
    <a v-on:click.once="listenToMyBoy">点击事件将只会触发一次</a>
    <input type="text" v-on:keyup.enter="listenToMyBoy" value=""/>


    <select v-model="selected">
      <option disabled value="">请选择</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
  <span>Selected: {{ selected }}</span>


  <comp v-bind:someprop="1"></comp>
  </div>
</template>

<script>
import Menu1 from './components/menu1'
import Foot from './components/foot'
import Comp from './components/comp'

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
        isShow:false,
        selected:''
      }
  },
  components: { // 注册组件才能使用,SelectItem Vue会把这个转化成 <select-item></select-item>
    Menu1, 
    Foot,
    Comp
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
