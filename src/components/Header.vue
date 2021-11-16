<template>
  <header class="flex">
    <h2>VueJS</h2>
    <p v-if="user" class="pointer" @click="setUser('')">Logout</p>
  </header>
</template>

<script>
export default {
  inject:['setUser','user']
}
</script>

<style scoped>
  header {
    justify-content: space-between;
    align-items: center;
    height:10vh;
    margin-bottom: 1rem;
    padding:0 1.5rem;
    color: white;
    background: #212529;
  }

  p {
    color:#1D77B5;
    text-decoration: underline;
  }

  h2 {
    font-weight: 400;
  }
</style>