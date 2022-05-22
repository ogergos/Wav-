girlWinter
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
};
</script>

<template>
  <header>
    <Nav />
  </header>

  <main>
    <h2 id="brandarticle">
      我們以潮流的腳步，走在時尚的浪潮中，
      希望以不同的角度，讓每個想要打造獨特風格的您，<br />
      都能找到屬於自己的穿搭方式！ 進而讓不同個性的人們開始熱愛這樣的購物樂趣。<br />
      Wav自1999年成立以來， 一直努力尋找最流行，最貼近時尚的潮流商品，<br />
      讓您能夠穿搭出屬於自己的獨特風格， 並且我們精心選擇品質優良的商品，<br />
      希望能帶給您最舒適的穿衣體驗， 經過多年的經營，我們在各平台已成為<br />
      大家所喜愛的熱門賣家之一， 我們相信一件時尚又舒適的衣服， 能為您帶來自信與魅力。<br />
      我們以您的角度出發，利用會員的制度，<br />
      給您最獨家的優惠！多元的商品打造出最適合您的造型風格。<br />
      最優質的服務及安全隱私交易流程， 成為讓您擁有最安心的購物饗宴。我們的用心，<br />
      您絕對看得見，讓您能自信的穿出屬於自已的風格態度，<br />
      歡迎將如此美好的經驗分享給身邊的好朋友們！
    </h2>
  </main>

  <footer>
    <Component1 />
  </footer>
</template>

<style>
@import "./assets/base.css";
#brandarticle {
  text-align: center;
  line-height: 3;
  font-weight: bold;
}
@media screen and (max-width: 1200px) {
  #brandarticle {
    font-size: 0.9rem;
  }
}
</style>
