<script>
export default {
  data() {
    return {
      imgs: [
        {
          src:
            "https://photo.whosewear.com/Upload/A947BF4C-C278-4E0D-B540-D7295B2ECC35/zh-cht/20220429153451097.jpg",
        },
        { src: "https://image.oshale.com.tw/banner/2022/20220503-001.jpg" },
        {
          src:
            "https://photo.whosewear.com/Upload/FDC00448-BFCC-400C-B122-C2C6C6B0E2E2/zh-cht/20220428152328953.jpg",
        },
        {
          src:
            "https://shoplineimg.com/623d35d0d6e4ab005b65d031/624efedf96ed3452fb0f0075/1200x.webp?source_format=jpg",
        },
        {
          src:
            "https://photo.whosewear.com/Upload/2B7FF7D2-A9BA-4B77-AF26-5908F70FE492/zh-cht/20220425145409306.jpg",
        },
      ],
      transitionName: "next",
      imgIndex: 0,
      imgCount: 3,
      imgStyle: {
        width: "100%",
        height: "600px",
      },
      Aleft: "-10%",
      Aright: "-10%",
      Atransition: "all 0.7s",
      startX: 0,
      moveX: 0,
    };
  },
  mounted() {
    setInterval(this.changeImg, 5000);
  },
  methods: {
    changeImg(add = 1) {
      if (add === 1 && this.imgIndex === this.imgs.length - 1) {
        this.imgIndex = 0;
      } else if (add === -1 && this.imgIndex === 0) {
        this.imgIndex = this.imgs.length - 1;
      } else {
        this.imgIndex = this.imgIndex + add;
      }
    },

    changeImgTo(objectIndex) {
      this.imgIndex = objectIndex;
    },

    showArrow() {
      this.Aleft = 0;
      this.Aright = 0;
      this.Atransition = "all 0.7s";
    },

    hideArrow() {
      this.Aleft = "-10%";
      this.Aright = "-10%";
      this.Atransition = "all 3s";
    },

    delayHide() {
      if (this.Aleft === 0) {
        setTimeout(this.hideArrow, 1200);
      }
    },
  },
  watch: {
    imgIndex(newIndex, oldIndex) {
      if (oldIndex === this.imgs.length - 1 && newIndex === 0) {
        this.transitionName = "next";
      } else if (oldIndex === 0 && newIndex === this.imgs.length - 1) {
        this.transitionName = "prev";
      } else {
        this.transitionName = newIndex > oldIndex ? "next" : "prev";
      }
    },
  },
};
</script>

<template>
  <Transition name="showArrow">
    <TransitionGroup
      tag="div"
      :name="transitionName"
      class="corrusel-wrapper"
      @mouseenter="showArrow"
      @mouseleave="delayHide"
    >
      <div
        v-for="(img, index) in imgs"
        :key="index"
        v-show="index === imgIndex"
        class="img-conainer"
        ref="imgList"
      >
        <img :src="img.src" alt="" :style="imgStyle" />
      </div>
      <slot name="arrow">
        <font-awesome-icon
          :icon="['fa', 'angle-left']"
          @click="changeImg(-1)"
          class="left-arrow"
          :style="{ left: Aleft, transition: Atransition }"
        />
        <font-awesome-icon
          :icon="['fa', 'angle-right']"
          @click="changeImg(1)"
          class="right-arrow"
          :style="{ right: Aright, transition: Atransition }"
        />
      </slot>
    </TransitionGroup>
  </Transition>
  <slot name="dot">
    <a href="#" v-for="n in imgs.length" :key="n - 1" class="dot-container">
      <font-awesome-icon
        :icon="['fa', 'circle']"
        @click="changeImgTo(n - 1)"
        v-if="n - 1 !== imgIndex"
        class="dot"
      />
      <font-awesome-icon
        :icon="['fa', 'circle']"
        @click="changeImgTo(n - 1)"
        v-else
        class="dot"
        style="color: black"
      />
    </a>
  </slot>
</template>

<style scoped>
.corrusel-wrapper {
  position: relative;
  overflow: hidden;
  margin: auto;
  width: 60%;
  height: 600px;
}
.img-conainer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 700px;
}
.left-arrow {
  position: absolute;
  top: 42%;
  font-size: 1rem;
  background-color: rgb(223, 2, 2);
  color: white;
  padding: 2.8em 1.1em;
}
.right-arrow {
  position: absolute;
  top: 42%;
  font-size: 1rem;
  background-color: rgb(223, 2, 2);
  color: white;
  padding: 2.8em 1.1em;
}
.dot-container {
  position: relative;
  top: 0;
  left: 45%;
  margin: 0 0.5em;
}
.dot {
  color: rgb(138, 61, 61);
  font-size: 0.7rem;
}

.next-enter-from {
  left: 100%;
}
.next-enter-active,
.next-leave-active {
  transition: all 0.1s ease;
}
.next-enter-to,
.next-leave-from {
  left: 0;
}
.next-leave-to {
  left: -100%;
}
.prev-enter-from {
  left: -100%;
}
.prev-enter-active,
.prev-leave-active {
  transition: all 0.1s ease;
}
.prev-enter-to,
.prev-leave-from {
  left: 0;
}
.prev-leave-to {
  left: 100%;
}
@media screen and (max-width: 1200px) {
  .corrusel-wrapper {
    width: 100%;
  }
}
</style>
