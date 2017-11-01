<template>
   <div>
			<h2>底部</h2>
			<span v-text="msgFromFather"></span>
			<button v-on:click="onClickMe">点击向父组件传递消息</button>
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
		onClickMe: function () {
			this.$emit('child-tell-me-something','来自子组件的消息');
		}
	}
}
</script>
