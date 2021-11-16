<template>
  <input ref="input" />  
</template>


<script>
export default {
 
}
</script>


<style scoped>
  input {
    width:250px;
    border: 1px solid #999;
    outline:none;
    padding:8px;
    border-radius: 5px;
    margin: 1.5rem 0;
  }
</style>
    <!-- :value="modelValue" @input="$emit('update:modelValue',$event.target.value)"  -->