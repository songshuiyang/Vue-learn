<template>
  <div class="hello">
    <input v-model="msg"/>

    <h2 v-on:click="setStore(msg)">设置LocalStorage</h2>
    <h2 v-on:click="getStore()">获得LocalStorage</h2>
    <!-- <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul> -->
  </div>
</template> 

<script>
import Store from '../store/store.js'

console.log(Store)  

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: '',
      item: []
    }
  },
  methods: {
    sayHello : function () {
      alert("11")
    },
    setStore : function (item) {
      Store.save(item)
    },
    getStore : function () {
      alert(Store.fetch())

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
