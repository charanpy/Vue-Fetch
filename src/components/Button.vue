<template>
  <button>
    <slot></slot>
  </button>
</template>


<style scoped>
 button {
   width:250px;
   border:none;
   outline:none;
   padding:9px;
   color:white;
   background: #212529;
   border-radius: 5px;
   cursor: pointer;
 }
 button:hover {
   background: black;
 }
</style>