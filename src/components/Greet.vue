<template>
  <h1 class="greet">
    <slot></slot>
  </h1>
</template>

<style scoped>
.greet {
  font-weight: 400;
  padding: 0 1.5rem;
  font-size: 18px;
}
</style>