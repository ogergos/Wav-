<script>
export default {
  props: {
    link: String,
    name: String,
    amount: Number,
  },
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
      <h3>
        訂單數量<a href="">{{ amount }}</a>
      </h3>
      <a href="#" @click="$emit('deleted')">取消訂單</a>
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
  margin: 0 3em;
}
.into-enter-active {
  transition: opacity 0.5s, left 1s;
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
    margin: 0 1em;
  }
}
</style>
