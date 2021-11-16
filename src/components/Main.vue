<template>
  <section class="main">
    <Header />
    <Greet>
      Welcome <b>{{ capitalizedUser }}</b>
    </Greet>
    <transition-group name="user" tag="section" class="cards">
      <User
        v-for="user in users"
        :key="user.id"
        :image="user.avatar"
        :name="user['first_name']"
        :email="user.email"
        :userId="user.id"
        @remove-user="removeUser"
      />
    </transition-group>

    <div class="flex flex-center">
      <Button class="btn" @click="loadUsers">LOAD MORE...</Button>
    </div>
  </section>
</template>

<script>
import Header from './Header.vue';
import User from './User.vue';
import Greet from './Greet.vue';
import Button from './Button.vue';

export default {
  data() {
    return {
      users: [],
      page: 1,
    };
  },
  computed: {
    capitalizedUser() {
      if (!this.user?.length) return;
      return `${this.user[0].toUpperCase()}${this.user.slice(1)}`
    }
  },
  props: {
    user: {
      type: String,
      default: '',
    },
  },
  methods: {
    getProducts(page = 0) {
      fetch(`https://reqres.in/api/users?page=${page || this.page}`)
        .then((res) => res.json())
        .then((json) => {
          this.users = this.users.concat(json.data);
        });
    },
    removeUser(userId) {
      if (!userId) return;
      this.users = this.users.filter((user) => user.id !== userId);
    },
    loadUsers() {
      this.page++;
      return this.getProducts(this.page);
    },
  },
  created() {
    this.getProducts();
  },
  components: {
    Header,
    User,
    Greet,
    Button,
  },
};
</script>

<style scoped>
.cards {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.user-item {
  display: inline-block;
  margin-right: 10px;
}
.user-enter-active,
.user-leave-active {
  transition: all 1s ease;
}
.user-enter-from,
.user-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.btn {
  width: fit-content !important;
}
.main {
  margin-bottom: 2rem;
}
</style>
