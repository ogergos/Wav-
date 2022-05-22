<script>
import Nav from "./components/Nav.vue";
import Corrusel1 from "./components/Corrusel1.vue";
import Item1 from "./components/Item1.vue";
import Component1 from "./components/Component1.vue";
import { store } from "./store.js";
export default {
  components: {
    Nav,
    Corrusel1,
    Item1,
    Component1,
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
};
</script>

<template>
  <header>
    <Nav />
  </header>

  <main>
    <h1 class="title">最新消息</h1>
    <Corrusel1 />
    <h1 class="title">限時搶購</h1>
    <div class="content">
      <Item1
        :link="this.$store.state.tmclothes[index].link"
        :name="this.$store.state.tmclothes[index].name"
        :gender="this.$store.state.tmclothes[index].gender"
        :type="this.$store.state.tmclothes[index].type"
        :price="this.$store.state.tmclothes[index].price"
        v-for="(item, index) in this.$store.state.tmclothes"
        :key="index"
        @add-to-shop="this.$store.commit('tmincrement', index)"
        class="imgList"
      />
    </div>
    <h1 class="title">每週新品</h1>
    <div class="content">
      <Item1
        :link="this.$store.state.weekclothes[index].link"
        :name="this.$store.state.weekclothes[index].name"
        :gender="this.$store.state.weekclothes[index].gender"
        :type="this.$store.state.weekclothes[index].type"
        :price="this.$store.state.weekclothes[index].price"
        v-for="(item, index) in this.$store.state.weekclothes"
        :key="index"
        @add-to-shop="this.$store.commit('weekincrement', index)"
        class="imgList"
      />
    </div>
  </main>

  <footer>
    <Component1 />
  </footer>
</template>

<style>
@import "./assets/base.css";
.title {
  text-align: center;
  margin: 1em 0;
  font-size: 3rem;
  font-weight: bold;
}
.content {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: flex-start;
  width: 60%;
  margin: auto;
}
.imgList {
  margin-right: 1em;
  width: 18%;
}
main {
  padding-bottom: 23em;
}
</style>
