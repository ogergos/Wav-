girlWinter
<script>
import Nav from "./components/Nav.vue";
import Component1 from "./components/Component1.vue";
import Item1 from "./components/Item1.vue";
import App3 from "./App3.vue";
export default {
  components: {
    Nav,
    Component1,
    Item1,
    App3,
  },

  data() {
    return {};
  },
  methods: {},
};
</script>

<template>
  <header>
    <Nav />
  </header>

  <main>
    <h1>客戶服務</h1>
    <p id="service-article">
      我們竭誠為客戶提供卓越的服務。<br />
      如果您有任何疑問，歡迎寄送電子郵件至 service.tw@esprit.com。 <br />
      我們的客服上班時間為：<br />
      <li class="service-span">週一至週五：上午 9:00 至下午 6:00</li>
      <li class="service-span">週六、週日及國定假日：無提供服務</li>
      請注意：我們的上班時間將根據台灣行事曆和時間 (CST) 。<br />
      我們絕不會因直接行銷目的而使用您的電子郵件，或將資訊分享給第三方廠商。請閱讀我們的隱私權政策全文，深入瞭解相關細節。
    </p>
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
#service-article {
  margin-top: 5em;
  line-height: 3;
  padding-left: 2em;
}
.service-span {
  font-size: 0.5rem;
}
</style>
