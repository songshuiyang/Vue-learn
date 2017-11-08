<template>
  <div>
    菜单
    <slot></slot>
  </div>
</template>
<script>
export default {
  name:'menu1',
  data: function (){
    return {
        item:''
    }
  },
}
</script>
