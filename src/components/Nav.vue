<script>
export default {
  data() {
    return {
      show0: false,
      show1: false,
      show2: false,
    };
  },
  methods: {
    showBar(index) {
      if (index === 0 && this.show1 === false) {
        this.show0 = true;
      } else if (index === 1 && this.show0 === false) {
        this.show1 = true;
      }
    },

    hideBar(index) {
      if (index === 0) {
        this.show0 = false;
      } else {
        this.show1 = false;
      }
    },

    showInput(index) {
      if (index === 0) {
        this.show2 = true;
      } else {
        this.show2 = false;
      }
    },
  },
};
</script>

<template>
  <div id="wrapper">
    <div id="container">
      <a href="index.html" id="icon">
        <font-awesome-icon :icon="['fa', 'shirt']" />
        WAV
      </a>
      <div id="type">
        <a href="" @mouseover="showBar(0)">男裝</a>
        <span>/</span>
        <a href="" @mouseover="showBar(1)">女裝</a>
      </div>
      <div id="shop">
        <a href="#" @click="showInput(0)" v-show="!show2"
          ><font-awesome-icon
            :icon="['fa', 'magnifying-glass']"
            style="margin-right: 0.5em"
          />搜尋商品</a
        >
        <input type="search" v-show="show2" @focusout="showInput(1)" v-model="text" />
        <a href="shoppingcar.html"
          ><font-awesome-icon
            :icon="['fa', 'bag-shopping']"
            style="margin-right: 0.5em"
          />購物車</a
        >
      </div>
    </div>
    <div class="navbar" v-show="show0" @mouseleave="hideBar(0)">
      <div>
        <img src="https://photo.whosewear.com/Photo/7ja-405/7ja-405-011.jpg" alt="" />
        <ul>
          <h3>上衣</h3>
          <li><a href="jacket.html">外套</a></li>
          <li><a href="longSleeve.html">長袖上衣</a></li>
          <li><a href="shortSleeve.html">短袖上衣</a></li>
        </ul>
      </div>
      <div>
        <img src="https://photo.whosewear.com/Photo/7ad-6799/7ad-6799-004.jpg" alt="" />
        <ul>
          <h3>下身</h3>
          <li><a href="shorts.html">短褲</a></li>
          <li><a href="pants.html">長褲</a></li>
        </ul>
      </div>
      <div>
        <img
          src="https://images.pexels.com/photos/343720/pexels-photo-343720.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260"
          alt=""
        />
        <ul>
          <h3><a href="summer.html">春夏精選</a></h3>
        </ul>
      </div>
      <div>
        <img
          src="https://images.pexels.com/photos/11902255/pexels-photo-11902255.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500"
          alt=""
        />
        <ul>
          <h3><a href="winter.html">秋冬精選</a></h3>
        </ul>
      </div>
    </div>
    <div class="navbar" v-show="show1" @mouseleave="hideBar(1)">
      <div>
        <img
          src="http://www.fashion-magic.com.tw/ezfiles/915/1915/plugin/ec/pictures/866/m/mczh-tw800x800_small69102.jpg"
          alt=""
        />
        <ul>
          <h3>上衣</h3>
          <li><a href="girlJacket.html">外套</a></li>
          <li><a href="girlLongclothes.html">長袖上衣</a></li>
          <li><a href="girlShortclothes.html">短袖上衣</a></li>
        </ul>
      </div>
      <div>
        <img
          src="http://www.fashion-magic.com.tw/ezfiles/915/1915/plugin/ec/pictures/463/m/mczh-tw800x800_small74602.gif"
          alt=""
        />
        <ul>
          <h3>下身</h3>
          <li><a href="girlShorts.html">短褲</a></li>
          <li><a href="girlPants.html">長褲</a></li>
          <li><a href="girlDress.html">裙裝</a></li>
        </ul>
      </div>
      <div>
        <img
          src="http://www.fashion-magic.com.tw/ezfiles/915/1915/plugin/ec/pictures/55/m/mczh-tw800x800_small74494.gif"
          alt=""
        />
        <ul>
          <h3><a href="girlSummer.html">春夏精選</a></h3>
        </ul>
      </div>
      <div>
        <img
          src="http://www.fashion-magic.com.tw/ezfiles/915/1915/plugin/ec/pictures/59/m/mczh-tw800x800_small69213.jpg"
          alt=""
        />
        <ul>
          <h3><a href="girlWinter.html">秋冬精選</a></h3>
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
#container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2em 5em;
  background-color: black;
  margin-bottom: 5em;
}
#container a {
  color: white;
}
#icon {
  font-size: 1.5rem;
  font-weight: bold;
  text-decoration: underline;
}
#type {
  font-size: 1.5rem;
  font-weight: bold;
}
#type a:hover {
  font-weight: bold;
  color: rgb(194, 64, 17);
  transition: color 0.2s;
}
span {
  color: white;
  margin: 0 1em;
}
#shop {
  display: flex;
  flex-direction: column;
}
#shop a:hover {
  text-decoration: underline;
}
#shop2 {
  display: none;
}
.navbar {
  display: flex;
  justify-content: flex-start;
}
.navbar > div {
  width: 25%;
  display: flex;
}
.navbar img {
  width: 100px;
}
.navbar a:hover {
  color: rgb(194, 64, 17);
}
.sortitem a {
  font-size: 0.5rem;
  margin: 0.5em;
}
@media screen and (max-width: 1200px) {
  #type {
    display: flex;
    flex-direction: column;
  }
  #type span {
    display: none;
  }
  .navbar {
    flex-direction: column;
  }
  .navbar > div {
    width: 100%;
    margin-bottom: 1em;
  }
  .navbar ul {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
  .navbar h3 {
    margin-right: 1em;
  }
  .navbar li {
    margin: 0 1.5em;
  }
}
</style>
