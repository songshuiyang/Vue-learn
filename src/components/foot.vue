<template>
   <div>
			<h2>底部</h2>
			<span v-text="msgFromFather"></span>
			<button v-on:click="onClickMe1">emit方式 点击向父组件传递消息</button>
			<button v-on:click="onClickMe2">dispatch方式 点击向父组件传递消息</button>
   </div>
</template>
<script>
export default {
  name:'foot',
  data: function (){
    return {
        item:''
    }
  },
	props:['msgFromFather'],
	methods: {
		onClickMe1: function () {
			this.$emit('child-tell-me-something','emit方式来自子组件的消息')
		},
		onClickMe2: function () {
			this.$dispatch('child-tell-me-something-dispatch','dispatch方式 点击向父组件传递消息')
		}
	}
}
</script>
