<template>
  <main>
    <Login v-if="!user.name"  />
    <Main v-else :user="user.name"></Main>
  </main>
</template>

<script>
import Login from "./components/Login.vue"
import Main from "./components/Main.vue"

export default {
  name: 'App',
  components: {
    Login,
    Main
  },
  data: function(){
    return {
      user: {
        name: ''
      }
    }
  },
  created() {
    const isUser = localStorage.getItem("vueUser");
    if (!isUser) return;
    this.user.name = isUser; 

  },
  methods:{
    setUser(username) {
      this.user.name = username
    }
  },
  provide:function() {
    return {
      user: this.user,
      setUser: this.setUser
    }
  }
}
</script>

<style>



* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.pointer {
  cursor: pointer;
}

.flex {
  display: flex;
}

.flex-column {
  display: flex;
  flex-direction: column;
}

.flex-center {
  align-items: center;
  justify-content: center;
}

.container {
  min-height: 90vh;
}
</style>
