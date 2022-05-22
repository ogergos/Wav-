<script>
import Nav from "./components/Nav.vue";
import Component1 from "./components/Component1.vue";
import Item3 from "./components/Item3.vue";
import { store } from "./store.js";
export default {
  components: {
    Nav,
    Component1,
    Item3,
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
  methods: {
    jkdel(index) {
      this.$store.state.jacket[index].order = 0;
    },
    tmdel(index) {
      this.$store.state.tmclothes[index].order = 0;
    },
    weekdel(index) {
      this.$store.state.weekclothes[index].order = 0;
    },
    longdel(index) {
      this.$store.state.longclothes[index].order = 0;
    },
    shortdel(index) {
      this.$store.state.stclothes[index].order = 0;
    },
    shortsdel(index) {
      this.$store.state.shorts1[index].order = 0;
    },

    pantsdel(index) {
      this.$store.state.pant[index].order = 0;
    },
    summerdel(index) {
      this.$store.state.summer1[index].order = 0;
    },

    winterdel(index) {
      this.$store.state.winter1[index].order = 0;
    },

    girlJacketdel(index) {
      this.$store.state.girlJacket1[index].order = 0;
    },

    girlLongclothesdel(index) {
      this.$store.state.girlLongclothes1[index].order = 0;
    },

    girlShortclothesdel(index) {
      this.$store.state.girlShortclothes1[index].order = 0;
    },

    girlShortsdel(index) {
      this.$store.state.girlShorts1[index].order = 0;
    },

    girlPantsdel(index) {
      this.$store.state.girlPants1[index].order = 0;
    },

    girlDressdel(index) {
      this.$store.state.girlDress1[index].order = 0;
    },

    girlSummerdel(index) {
      this.$store.state.girlSummer1[index].order = 0;
    },

    girlWinterdel(index) {
      this.$store.state.girlWinter1[index].order = 0;
    },
  },
};
</script>

<template>
  <header>
    <Nav />
  </header>

  <main>
    <div>
      <h1 id="order-title">訂單已經成立，請耐心等候商品送達</h1>

      <div
        v-for="(item, index) in this.$store.state.jacket"
        :key="index"
        v-show="this.$store.state.jacket[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.jacket[index].link"
          :name="this.$store.state.jacket[index].name"
          :amount="this.$store.state.jacket[index].order"
          @deleted="jkdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.tmclothes"
        :key="index"
        v-show="this.$store.state.tmclothes[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.tmclothes[index].link"
          :name="this.$store.state.tmclothes[index].name"
          :amount="this.$store.state.tmclothes[index].order"
          @deleted="tmdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.weekclothes"
        :key="index"
        v-show="this.$store.state.weekclothes[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.weekclothes[index].link"
          :name="this.$store.state.weekclothes[index].name"
          :amount="this.$store.state.weekclothes[index].order"
          @deleted="weekdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.longclothes"
        :key="index"
        v-show="this.$store.state.longclothes[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.longclothes[index].link"
          :name="this.$store.state.longclothes[index].name"
          :amount="this.$store.state.longclothes[index].order"
          @deleted="longdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.stclothes"
        :key="index"
        v-show="this.$store.state.stclothes[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.stclothes[index].link"
          :name="this.$store.state.stclothes[index].name"
          :amount="this.$store.state.stclothes[index].order"
          @deleted="shortdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.shorts1"
        :key="index"
        v-show="this.$store.state.shorts1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.shorts1[index].link"
          :name="this.$store.state.shorts1[index].name"
          :amount="this.$store.state.shorts1[index].order"
          @deleted="shortsdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.pant"
        :key="index"
        v-show="this.$store.state.pant[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.pant[index].link"
          :name="this.$store.state.pant[index].name"
          :amount="this.$store.state.pant[index].order"
          @deleted="pantsdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.summer1"
        :key="index"
        v-show="this.$store.state.summer1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.summer1[index].link"
          :name="this.$store.state.summer1[index].name"
          :amount="this.$store.state.summer1[index].order"
          @deleted="summerdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.winter1"
        :key="index"
        v-show="this.$store.state.winter1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.winter1[index].link"
          :name="this.$store.state.winter1[index].name"
          :amount="this.$store.state.winter1[index].order"
          @deleted="winterdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlJacket1"
        :key="index"
        v-show="this.$store.state.girlJacket1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlJacket1[index].link"
          :name="this.$store.state.girlJacket1[index].name"
          :amount="this.$store.state.girlJacket1[index].order"
          @deleted="girlJacketdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlLongclothes1"
        :key="index"
        v-show="this.$store.state.girlLongclothes1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlLongclothes1[index].link"
          :name="this.$store.state.girlLongclothes1[index].name"
          :amount="this.$store.state.girlLongclothes1[index].order"
          @deleted="girlLongclothesdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlShortclothes1"
        :key="index"
        v-show="this.$store.state.girlShortclothes1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlShortclothes1[index].link"
          :name="this.$store.state.girlShortclothes1[index].name"
          :amount="this.$store.state.girlShortclothes1[index].order"
          @deleted="girlShortclothesdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlShorts1"
        :key="index"
        v-show="this.$store.state.girlShorts1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlShorts1[index].link"
          :name="this.$store.state.girlShorts1[index].name"
          :amount="this.$store.state.girlShorts1[index].order"
          @deleted="girlShortsdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlPants1"
        :key="index"
        v-show="this.$store.state.girlPants1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlPants1[index].link"
          :name="this.$store.state.girlPants1[index].name"
          :amount="this.$store.state.girlPants1[index].order"
          @deleted="girlPantsdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlDress1"
        :key="index"
        v-show="this.$store.state.girlDress1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlDress1[index].link"
          :name="this.$store.state.girlDress1[index].name"
          :amount="this.$store.state.girlDress1[index].order"
          @deleted="girlDressdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlSummer1"
        :key="index"
        v-show="this.$store.state.girlSummer1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlSummer1[index].link"
          :name="this.$store.state.girlSummer1[index].name"
          :amount="this.$store.state.girlSummer1[index].order"
          @deleted="girlSummerdel(index)"
          class="imgList"
        />
      </div>

      <div
        v-for="(item, index) in this.$store.state.girlWinter1"
        :key="index"
        v-show="this.$store.state.girlWinter1[index].order >= 1"
        class="content2"
      >
        <Item3
          :link="this.$store.state.girlWinter1[index].link"
          :name="this.$store.state.girlWinter1[index].name"
          :amount="this.$store.state.girlWinter1[index].order"
          @deleted="girlWinterdel(index)"
          class="imgList"
        />
      </div>
    </div>
  </main>

  <footer>
    <Component1 />
  </footer>
</template>

<style>
@import "./assets/base.css";
#order-title {
  text-align: center;
  animation: show 2s ease-in-out;
  animation-fill-mode: forwards;
}
.content2 {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: flex-start;
  width: 80%;
  margin: 5em auto;
}
@keyframes show {
  from {
    opacity: 100%;
  }
  to {
    opacity: 0;
  }
}
@media screen and (max-width: 1200px) {
  .content2 {
    width: 100%;
    font-size: 0.5rem;
  }
}
</style>
