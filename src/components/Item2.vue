<script>
export default {
  props: {
    link: String,
    name: String,
    price: String,
    amount: Number,
    total: String,
  },
  emits: ["deleted", "order"],
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
};
</script>

<template>
  <Transition name="into">
    <div v-show="show">
      <img :src="link" alt="" />
      <h4>{{ name }}</h4>
      <h3 style="color: rgb(155, 39, 39)">價格 {{ price }}</h3>
      <h3>
        數量<a href="">{{ amount }}</a>
      </h3>
      <h3>總共 {{ total }}</h3>
      <a href="#" @click="$emit('deleted')">刪除</a>
      <a href="order.html" id="buy" @click="$emit('order')">前往結帳</a>
    </div>
  </Transition>
</template>

<style scoped>
div {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  height: 200px;
  width: 100%;
  margin: 4em 0;
  border-top: 10px solid rgb(107, 98, 98);
  border-bottom: 10px solid rgb(150, 138, 138);
  padding: 2em 0;
  position: relative;
  left: 0;
}
img {
  width: 141px;
}
h4 {
  align-self: flex-start;
  margin-right: 4em;
  margin-left: 1em;
  width: 200px;
}
h3 {
  margin: 0 1em;
}
a {
  display: inline-block;
  padding: 0.5em 1em;
  background-color: rgb(199, 199, 199);
  margin: 0 1.5em;
}
#buy {
  color: white;
  background-color: black;
}
.into-enter-active {
  transition: opacity 1s, left 1s;
}
.into-enter-from {
  opacity: 0;
  left: -20%;
}
.into-enter-to {
  opacity: 1;
  left: 0;
}
@media screen and (max-width: 1200px) {
  a {
    margin: 0;
  }
  h4 {
    margin-right: 1em;
  }
}
</style>
