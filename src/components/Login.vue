<template>
<Header />
  <section class="flex-column flex-center container">
    <h1>LOGIN</h1>
    <form class="flex-column" @submit.prevent="submit">
      <Input ref="user" placeholder="Username" />
      <Button type="submit">LOGIN</Button>
    </form>
  </section>
</template>

<script>
import Input from './Input.vue';
import Button from './Button.vue';
import Header from './Header.vue';
export default {
  components: {
    Input,
    Button,
    Header,
  },
  inject:['setUser'],
  methods: {
    submit() {
      const username = this.$refs.user.$refs.input.value;
      if (!username) return alert("nope")
      localStorage.setItem("vueUser",username);
      this.setUser(username)
    }
  }
  
};
</script>

<style scoped></style>
