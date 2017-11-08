<template>
   <div>
       comp组件
			 {{someprop}}
   </div>
</template>
<script>
export default {
	name:'comp',
	data: function (){
    return {
        item:''
    }
	},
	props:['someprop']



}


</script>