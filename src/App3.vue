<script>
import Nav from "./components/Nav.vue";
import Component1 from "./components/Component1.vue";
import Item1 from "./components/Item1.vue";
import Item2 from "./components/Item2.vue";
import { store } from "./store.js";
export default {
  components: {
    Nav,
    Component1,
    Item1,
    Item2,
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
      this.$store.state.jacket[index].count = 0;
    },

    tmdel(index) {
      this.$store.state.tmclothes[index].count = 0;
    },

    weekdel(index) {
      this.$store.state.weekclothes[index].count = 0;
    },

    longdel(index) {
      this.$store.state.longclothes[index].count = 0;
    },

    shortdel(index) {
      this.$store.state.stclothes[index].count = 0;
    },

    shortsdel(index) {
      this.$store.state.shorts1[index].count = 0;
    },

    pantsdel(index) {
      this.$store.state.pant[index].count = 0;
    },

    summerdel(index) {
      this.$store.state.summer1[index].count = 0;
    },

    winterdel(index) {
      this.$store.state.winter1[index].count = 0;
    },

    girlJacketdel(index) {
      this.$store.state.girlJacket1[index].count = 0;
    },

    girlLongclothesdel(index) {
      this.$store.state.girlLongclothes1[index].count = 0;
    },

    girlShortclothesdel(index) {
      this.$store.state.girlShortclothes1[index].count = 0;
    },

    girlShortsdel(index) {
      this.$store.state.girlShorts1[index].count = 0;
    },

    girlPantsdel(index) {
      this.$store.state.girlPants1[index].count = 0;
    },

    girlDressdel(index) {
      this.$store.state.girlDress1[index].count = 0;
    },

    girlSummerdel(index) {
      this.$store.state.girlSummer1[index].count = 0;
    },

    girlWinterdel(index) {
      this.$store.state.girlWinter1[index].count = 0;
    },
  },
};
</script>

<template>
  <header>
    <Nav />
  </header>

  <main>
    <div
      v-for="(item, index) in this.$store.state.jacket"
      :key="index"
      v-show="this.$store.state.jacket[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.jacket[index].link"
        :name="this.$store.state.jacket[index].name"
        :price="this.$store.state.jacket[index].price"
        :amount="this.$store.state.jacket[index].count"
        :total="
          'NT$' +
          this.$store.state.jacket[index].numberprice *
            this.$store.state.jacket[index].count
        "
        @deleted="jkdel(index)"
        @order="this.$store.commit('jkaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.tmclothes"
      :key="index"
      v-show="this.$store.state.tmclothes[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.tmclothes[index].link"
        :name="this.$store.state.tmclothes[index].name"
        :price="this.$store.state.tmclothes[index].price"
        :amount="this.$store.state.tmclothes[index].count"
        :total="
          'NT$' +
          this.$store.state.tmclothes[index].numberprice *
            this.$store.state.tmclothes[index].count
        "
        @deleted="tmdel(index)"
        @order="this.$store.commit('tmaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.weekclothes"
      :key="index"
      v-show="this.$store.state.weekclothes[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.weekclothes[index].link"
        :name="this.$store.state.weekclothes[index].name"
        :price="this.$store.state.weekclothes[index].price"
        :amount="this.$store.state.weekclothes[index].count"
        :total="
          'NT$' +
          this.$store.state.weekclothes[index].numberprice *
            this.$store.state.weekclothes[index].count
        "
        @deleted="weekdel(index)"
        @order="this.$store.commit('weekaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.longclothes"
      :key="index"
      v-show="this.$store.state.longclothes[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.longclothes[index].link"
        :name="this.$store.state.longclothes[index].name"
        :price="this.$store.state.longclothes[index].price"
        :amount="this.$store.state.longclothes[index].count"
        :total="
          'NT$' +
          this.$store.state.longclothes[index].numberprice *
            this.$store.state.longclothes[index].count
        "
        @deleted="longdel(index)"
        @order="this.$store.commit('longsleeveaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.stclothes"
      :key="index"
      v-show="this.$store.state.stclothes[index].count >= 1"
      class="content1"
    >
      <Item2shorts
        :link="this.$store.state.stclothes[index].link"
        :name="this.$store.state.stclothes[index].name"
        :price="this.$store.state.stclothes[index].price"
        :amount="this.$store.state.stclothes[index].count"
        :total="
          'NT$' +
          this.$store.state.stclothes[index].numberprice *
            this.$store.state.stclothes[index].count
        "
        @deleted="shortdel(index)"
        @order="this.$store.commit('shortsleeveaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.shorts1"
      :key="index"
      v-show="this.$store.state.shorts1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.shorts1[index].link"
        :name="this.$store.state.shorts1[index].name"
        :price="this.$store.state.shorts1[index].price"
        :amount="this.$store.state.shorts1[index].count"
        :total="
          'NT$' +
          this.$store.state.shorts1[index].numberprice *
            this.$store.state.shorts1[index].count
        "
        @deleted="shortsdel(index)"
        @order="this.$store.commit('shortsaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.pant"
      :key="index"
      v-show="this.$store.state.pant[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.pant[index].link"
        :name="this.$store.state.pant[index].name"
        :price="this.$store.state.pant[index].price"
        :amount="this.$store.state.pant[index].count"
        :total="
          'NT$' +
          this.$store.state.pant[index].numberprice * this.$store.state.pant[index].count
        "
        @deleted="pantsdel(index)"
        @order="this.$store.commit('pantsaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.summer1"
      :key="index"
      v-show="this.$store.state.summer1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.summer1[index].link"
        :name="this.$store.state.summer1[index].name"
        :price="this.$store.state.summer1[index].price"
        :amount="this.$store.state.summer1[index].count"
        :total="
          'NT$' +
          this.$store.state.summer1[index].numberprice *
            this.$store.state.summer1[index].count
        "
        @deleted="summerdel(index)"
        @order="this.$store.commit('summeraddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.winter1"
      :key="index"
      v-show="this.$store.state.winter1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.winter1[index].link"
        :name="this.$store.state.winter1[index].name"
        :price="this.$store.state.winter1[index].price"
        :amount="this.$store.state.winter1[index].count"
        :total="
          'NT$' +
          this.$store.state.winter1[index].numberprice *
            this.$store.state.winter1[index].count
        "
        @deleted="winterdel(index)"
        @order="this.$store.commit('winteraddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlJacket1"
      :key="index"
      v-show="this.$store.state.girlJacket1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlJacket1[index].link"
        :name="this.$store.state.girlJacket1[index].name"
        :price="this.$store.state.girlJacket1[index].price"
        :amount="this.$store.state.girlJacket1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlJacket1[index].numberprice *
            this.$store.state.girlJacket1[index].count
        "
        @deleted="girlJacketdel(index)"
        @order="this.$store.commit('girlJacketaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlLongclothes1"
      :key="index"
      v-show="this.$store.state.girlLongclothes1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlLongclothes1[index].link"
        :name="this.$store.state.girlLongclothes1[index].name"
        :price="this.$store.state.girlLongclothes1[index].price"
        :amount="this.$store.state.girlLongclothes1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlLongclothes1[index].numberprice *
            this.$store.state.girlLongclothes1[index].count
        "
        @deleted="girlLongclothesdel(index)"
        @order="this.$store.commit('girlLongclothesaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlShortclothes1"
      :key="index"
      v-show="this.$store.state.girlShortclothes1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlShortclothes1[index].link"
        :name="this.$store.state.girlShortclothes1[index].name"
        :price="this.$store.state.girlShortclothes1[index].price"
        :amount="this.$store.state.girlShortclothes1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlShortclothes1[index].numberprice *
            this.$store.state.girlShortclothes1[index].count
        "
        @deleted="girlShortclothesdel(index)"
        @order="this.$store.commit('girlShortclothesaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlShorts1"
      :key="index"
      v-show="this.$store.state.girlShorts1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlShorts1[index].link"
        :name="this.$store.state.girlShorts1[index].name"
        :price="this.$store.state.girlShorts1[index].price"
        :amount="this.$store.state.girlShorts1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlShorts1[index].numberprice *
            this.$store.state.girlShorts1[index].count
        "
        @deleted="girlShortsdel(index)"
        @order="this.$store.commit('girlShortsaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlPants1"
      :key="index"
      v-show="this.$store.state.girlPants1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlPants1[index].link"
        :name="this.$store.state.girlPants1[index].name"
        :price="this.$store.state.girlPants1[index].price"
        :amount="this.$store.state.girlPants1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlPants1[index].numberprice *
            this.$store.state.girlPants1[index].count
        "
        @deleted="girlPantsdel(index)"
        @order="this.$store.commit('girlPantsaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlDress1"
      :key="index"
      v-show="this.$store.state.girlDress1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlDress1[index].link"
        :name="this.$store.state.girlDress1[index].name"
        :price="this.$store.state.girlDress1[index].price"
        :amount="this.$store.state.girlDress1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlDress1[index].numberprice *
            this.$store.state.girlDress1[index].count
        "
        @deleted="girlDressdel(index)"
        @order="this.$store.commit('girlDressaddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlSummer1"
      :key="index"
      v-show="this.$store.state.girlSummer1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlSummer1[index].link"
        :name="this.$store.state.girlSummer1[index].name"
        :price="this.$store.state.girlSummer1[index].price"
        :amount="this.$store.state.girlSummer1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlSummer1[index].numberprice *
            this.$store.state.girlSummer1[index].count
        "
        @deleted="girlSummerdel(index)"
        @order="this.$store.commit('girlSummeraddOrder', index)"
        class="imgList"
      />
    </div>

    <div
      v-for="(item, index) in this.$store.state.girlWinter1"
      :key="index"
      v-show="this.$store.state.girlWinter1[index].count >= 1"
      class="content1"
    >
      <Item2
        :link="this.$store.state.girlWinter1[index].link"
        :name="this.$store.state.girlWinter1[index].name"
        :price="this.$store.state.girlWinter1[index].price"
        :amount="this.$store.state.girlWinter1[index].count"
        :total="
          'NT$' +
          this.$store.state.girlWinter1[index].numberprice *
            this.$store.state.girlWinter1[index].count
        "
        @deleted="girlWinterdel(index)"
        @order="this.$store.commit('girlWinteraddOrder', index)"
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
.imgList {
  margin-right: 1em;
  width: 18%;
}
.content1 {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: flex-start;
  width: 80%;
  margin: 5em auto;
}
@media screen and (max-width: 1200px) {
  .content1 {
    width: 100%;
    font-size: 0.5rem;
  }
}
</style>
