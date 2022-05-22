<script>
export default {
    data() {
        return {
            imgs: [
                { src: "https://images.pexels.com/photos/572056/pexels-photo-572056.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500", title: "企業最佳數位轉型技術夥伴", content: "看5xRuby協助新加坡知名倉儲平台，將實體空間轉化為共享經濟的一環，擴大商機" },
                { src: "https://images.pexels.com/photos/220357/pexels-photo-220357.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500", title: "從開發到部署的整合技術專家", content: "看5xRuby協助新加坡知名倉儲平台，將實體空間轉化為共享經濟的一環，擴大商機" },
                { src: "https://images.pexels.com/photos/1109543/pexels-photo-1109543.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500", title: "以最精練的開發能量解決最困難的事", content: "看5xRuby協助新加坡知名倉儲平台，將實體空間轉化為共享經濟的一環，擴大商機" },
                { src: "https://images.pexels.com/photos/463684/pexels-photo-463684.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500", title: "協助企業開發更穩定流暢的服務", content: "看5xRuby協助新加坡知名倉儲平台，將實體空間轉化為共享經濟的一環，擴大商機" },
            ],
            transitionName: "next",
            imgIndex: 0,
            imgCount: 3,
            imgStyle: {
                width: '80%',
            },
            Aleft: '-10%',
            Aright: '-10%',
            Atransition: 'all 0.7s',
            startX: 0,
            moveX: 0,
        }
    },
    mounted() {
        
    },
    methods: {
        changeImg(add = 1) {
            if(add === 1 && this.imgIndex === this.imgs.length - 1) {
                this.imgIndex = 0;
            } else if(add === -1 && this.imgIndex === 0) {
                this.imgIndex = this.imgs.length -1
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
            this.Atransition = 'all 0.7s'
        },

        hideArrow() {
            this.Aleft = '-10%';
            this.Aright = '-10%';
            this.Atransition = 'all 3s'
        },

        delayHide() {
            setTimeout(this.hideArrow, 1200);
        },

        startDrag(e) {
            this.startX = e.pageX;
        },

        draging(e) {
            this.moveX = e.pageX;
        },

        stopDrag() {
            if(this.moveX - this.startX > 100) {
                if(this.imgIndex === 0) {
                    this.imgIndex = this.imgs.length - 1; 
                } else {
                    this.imgIndex--;
                }
            } else if(this.moveX - this.startX < -100) {
                if(this.imgIndex === this.imgs.length - 1) {
                    this.imgIndex = 0;
                } else {
                    this.imgIndex++;
                }
            } else{
                return;
            }
        }
    },
    watch: {
        imgIndex(newIndex, oldIndex) {
            if(oldIndex === this.imgs.length - 1 && newIndex === 0) {
                this.transitionName = "next";
            } else if(oldIndex === 0 && newIndex === this.imgs.length - 1) {
                this.transitionName = "prev";
            } else {
                this.transitionName = newIndex > oldIndex ? "next" : "prev";
            }
        }
    }
}
</script>

<template>
    <Transition name="showArrow">
        <TransitionGroup tag="div" :name="transitionName" class="corrusel-wrapper" @mouseenter="showArrow" @mousedown="startDrag" @mousemove="draging" @mouseup="stopDrag" ref="wrap">
            <div v-for="(img, index) in imgs" :key="index" v-show="index === imgIndex" class="img-conainer" ref="imgList">
                <img :src="img.src" alt="" :style="imgStyle" >
            </div>
            <div class="imgText" v-for="(img, index) in imgs" :key="index" v-show="index === imgIndex">
                    <h1>{{ img.title }}</h1>
                    <p>{{ img.content }}</p>
                    <a href="">看更多</a>
            </div>
            <slot name="arrow">
                <font-awesome-icon :icon="['fa', 'angle-left']" @click="changeImg(-1)" class="left-arrow" :style="{ left: Aleft, transition: Atransition}"/>
                <font-awesome-icon :icon="['fa', 'angle-right']" @click="changeImg(1)" class="right-arrow" :style="{ right: Aright, transition: Atransition}"/>
            </slot>
        </TransitionGroup>
    </Transition>
    <slot name="dot">
         <div href="#" v-for="n in imgs.length" :key="n - 1" class="dot-container">
            <div @click="changeImgTo(n - 1)" class="dot" v-if="n-1 !== imgIndex">
            </div>
            <div class="red" v-if="n-1 === imgIndex"></div>
        </div>
    </slot>
</template>

<style scoped>
.corrusel-wrapper{
    overflow: hidden;
    margin: 10em auto;
    width: 100%;
    height: 500px;
    top: 0;
    left: 0;
    display: flex;
    justify-content: space-between;
    padding: 0 10em;
}
.img-conainer{
    width: 100%;
}
.imgText{
    color: black;
    display: flex;
    flex-wrap: wrap;
}
.left-arrow{
    position: absolute;
    top: 42%;
    font-size: 1rem;
    background-color: rgb(223, 2, 2);
    color: white;
    padding: 2.8em 1.1em;
}
.right-arrow{
    position: absolute;
    top: 42%;
    font-size: 1rem;
    background-color: rgb(223, 2, 2);
    color: white;
    padding: 2.8em 1.1em;   
}
.dot-container{
    position: relative;
    bottom: 50px;
    left: 20%;
    margin: 0 2em;
    display: inline-block;
}
.dot{
    width: 50px;
    height: 2px;
    background-color: black;
    position: absolute;
    top: 0;
    left: 0;
    display: inline-block;
}
.red{
    width: 50px;
    height: 5px;
    background-color: red;
    position: absolute;
    top: -2px;
    left: 0;
    display: inline-block;
    z-index: 1;
}
.img-title-container{
    width: 100%;
    padding: 0;
}
.img-title-container img{
    width: 40px;
    margin-right: 1em;
}
.img-title-container a{
    display: inline-block;
    width: 20%;
    color: black;
    text-decoration: none;
    font-size: 0.8rem;
    border-right: 1px dotted rgb(184, 184, 184);
    padding-left: 1em;
}
.img-title-container span{
    position: absolute;
    top: 30%;
    bottom: 0;
}
.img-title-container span:hover{
    color: rgb(223, 2, 2);
}
.line{
    width: 0;
    height: 3px;
    background-color: rgb(223, 2, 2);
    display: inline-block;
    margin: 0;
    padding: 0;
}
.next-enter-from{
    left: 100%;
}
.next-enter-active,
.next-leave-active{
    transition: all 0.1s ease;
}
.next-enter-to,
.next-leave-from{
    left: 0;
}
.next-leave-to{
    left: -100%;
}
.prev-enter-from{
    left: -100%;
}
.prev-enter-active,
.prev-leave-active{
    transition: all 0.1s ease;
}
.prev-enter-to,
.prev-leave-from{
    left: 0;
}
.prev-leave-to{
    left: 100%;
}
.shadow-enter-active,
.shadow-leave-active{
    transition: all 0.4s;
}
.shadow-enter-from,
.shadow-leave-to{
    opacity: 0;
}
.shadow-enter-to,
.shadow-leave-from{
    opacity: 100%;
}
@media screen and (max-width: 768px) {
    .corrusel-wrapper{
        display: flex;
        flex-flow: column wrap;
        justify-content: center;
        align-items: center;
    }
}
</style>