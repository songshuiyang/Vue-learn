<template>
  
   <div>
			<h2>底部</h2>
			<span v-text="msgFromFather"></span>
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
  props:['msgFromFather']
}
</script>
