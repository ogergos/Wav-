<script>
import Nav from "./components/Nav.vue";
import Component1 from "./components/Component1.vue";
import Item1 from "./components/Item1.vue";
import App3 from "./App3.vue";
import { store } from "./store.js";
export default {
  components: {
    Nav,
    Component1,
    Item1,
    App3,
  },

  data() {
    return {
      store,
    };
  },
  mounted() {
    window.addEventListener("beforeunload", () => {
      localStorage.setItem("store", JSON.stringify(this.$store.state));
    });
  },
  created() {
    if (localStorage.getItem("store")) {
      this.$store.replaceState(
        Object.assign({}, this.$store.state, JSON.parse(localStorage.getItem("store")))
      );
    }
  },
  methods: {},

  computed: {
    sortItem() {
      this.$store.state.jacket.sort((a, b) => a.numberprice - b.numberprice);
    },
    sortItem1() {
      this.$store.state.jacket.sort((a, b) => b.numberprice - a.numberprice);
    },
    sortItem2() {
      this.$store.state.jacket.sort(() => 0.5 - Math.random());
    },
  },
};
</script>

<template>
  <header>
    <Nav />
  </header>

  <main>
    <h1>外套類</h1>
    <div class="sortitem">
      <h3>價格排序</h3>
      <a href="#" style="color: orange" @click="sortItem1">高到低</a
      ><a href="#" style="color: orange" @click="sortItem">低到高</a>
      <a href="" style="color: orange" @click="sortItem2">隨機</a>
    </div>
    <div class="content">
      <TransitionGroup name="show">
        <Item1
          :link="this.$store.state.jacket[index].link"
          :name="this.$store.state.jacket[index].name"
          :gender="this.$store.state.jacket[index].gender"
          :type="this.$store.state.jacket[index].type"
          :price="this.$store.state.jacket[index].price"
          v-for="(item, index) in this.$store.state.jacket"
          :key="index"
          class="imgList"
          @add-to-shop="this.$store.commit('jkincrement', index)"
        />
      </TransitionGroup>
    </div>
  </main>

  <footer>
    <Component1 />
  </footer>
</template>

<style>
@import "./assets/base.css";
h1 {
  text-align: center;
  font-size: 3rem;
  font-weight: bold;
}
.imgList {
  margin-right: 1em;
  width: 18%;
}
.content {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: flex-start;
  width: 60%;
  margin: 5em auto;
}
.show-enter-active {
  transition: all 0.5s;
}
.show-enter-from {
  opacity: 0;
}
.show-enter-to {
  opacity: 1;
}
</style>
