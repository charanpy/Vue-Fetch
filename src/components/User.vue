<template>
  <div class="card flex-column flex-center">
    <div>
      <img :src="image" />
    </div>
    <div class="flex-column flex-center">
      <h2>{{ name }}</h2>
      <p>{{ email }}</p>
      <p class="remove pointer" @click="remove">&#x2715;</p>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['removeUser'],
  props: {
    image: String,
    name: String,
    email: String,
    userId: Number,
  },
  methods: {
    remove() {
      this.$emit('removeUser', this.userId);
    },
  },
};
</script>

<style scoped>
img {
  width: 100px;
  object-fit: cover;
  border-radius: 50%;
}
.card {
  box-shadow: 0 15px 30px 1px grey;
  background: rgba(255, 255, 255, 0.9);
  width: 400px;
  padding: 1.5rem;
  line-height: 1.8;
  border-radius: 5px;
  margin: 2rem 0;
  position: relative;
}

.remove {
  position: absolute;
  right: 3%;
  top: 3%;
  color: red;
  font-weight: bolder;
  font-size: 20px;
}
</style>
