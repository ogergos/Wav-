<script>
export default {
  props: {
    link: String,
    gender: String,
    type: String,
    name: String,
    price: String,
  },
  emits: ["addToShop"],
  data() {
    return {
      show: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.show = true;
    }, 10);
  },
  methods: {},
};
</script>

<template>
  <Transition>
    <div v-show="show">
      <img :src="link" alt="" />
      <h4>{{ name }}</h4>
      <h5>{{ gender }}</h5>
      <h5>{{ type }}</h5>
      <h2>{{ price }}</h2>
      <a href="shoppingcar.html" @click="$emit('addToShop')">立即購買</a>
    </div>
  </Transition>
</template>

<style scoped>
div {
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: flex-start;
}
img {
  width: 150px;
  height: 200px;
}
a {
  border: 2px solid rgb(97, 41, 41);
  display: inline-block;
  padding: 0.5em 1em;
}
a:hover {
  color: white;
  background-color: rgb(97, 41, 41);
  transition: background-color 0.1s;
}
h2 {
  color: rgb(155, 39, 39);
}
.v-enter-active {
  transition: opacity 1s;
}
.v-enter-from {
  opacity: 0;
}
.v-enter-to {
  opacity: 1;
}
@media screen and (max-width: 1200px) {
  div {
    width: 150px;
  }
}
</style>
