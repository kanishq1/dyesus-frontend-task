<template>
<div class="carousel">
  <div class="slides">
    <transition-group 
      name="slide"
      mode="out-in"
      enter-class="slide-in"
      leave-class="slide-out"
      enter-active-class="animated slide-in-active"
      leave-active-class="animated slide-out-active"
    >
      <div
        v-for="slide in slides1"
        :key="slide.id"
      >
      <div>
        <!-- <h1 v-if="slide.id == active">Slides {{slide.title}}</h1> -->
        <img :src="slide.title" v-if="slide.id == active" class="product-main-img" alt="Img not there"/>
      </div>
      
      </div>
    </transition-group>
  </div>
  <ul class="dots">
    <li 
      v-for="(dot,slide) in slides"
      :key='slide.id'
      :class="{ active: dot === active }"
      @click="jump(dot)"
    ></li>
  </ul>
  </div>
</template>

<script>
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'
export default {
  name: 'ProductCarousel',
  data: function(){
        return {
          slides: 3,
          slides1: [
            {
              title: 'https://ik.imagekit.io/enactus/Group_316_L1JjbffS-.png',
              id: 1
            },
            {
              title: '',
              id: 2
            },
            {
              title: 'https://ik.imagekit.io/enactus/Group_316_L1JjbffS-.png',
              id: 3
            }
          ],
          active: 1
  }},
  methods: {
    move(amount) {
      let newActive
      const newIndex = this.active + amount
      if (newIndex > this.slides) newActive = 1
      if (newIndex === 0) newActive = this.slides
      this.active = newActive || newIndex
    },
    jump(index) {
      this.active = index
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$primary: #221e21;

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
}

body {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  color: $primary;
}

.prev,
.next {
  position: absolute;
  top: 50%;
  width: 20px;
  height: 20px;
  border: 2px solid $primary;
  color: $primary;
  border-radius: 50%;
  margin-top: -25px;
  margin-left: 25px;
  cursor: pointer;
  line-height: 48px;
  text-align: center;
  text-indent: -2px;
  transition: all 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  
  &:hover {
    background: $primary;
    color: #fff;
    transform: scale(1.2);
  }
  
  &:active {
    transform: translate(0, 3px) scale(1.2);
  }
}
.prev{
  left: 0;
}
.next {
  right: 0;
  margin-left: auto;
  margin-right: 25px;
  text-indent: 2px;
}
.product-main-img{
  min-height: 240px;
  padding: 10px 0;
}
.dots {
  display: block;
  width: 100%;
  text-align: center;
  bottom: 20px;
  
  li {
    width: 6px;
    height: 6px;
    border-radius: 3px;
    background: #000000 30%;
    opacity: 0.2;
    display: inline-block;
    margin: 0 3px;
    cursor: pointer;
    transition: opacity 0.4s ease-in-out,width 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    
    &.active {
      background: #F8D702;
      width: 38px;
      opacity: 1;
    }
  }
}

.slides {
  margin: auto;
  background: #C4C4C4;
  box-shadow: 0px 3px 10px #d0d0d0;
  border-radius: 7px;
  width:90vw;
  font-size: 40px;
  display: flex;
  height: 100%;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  
  @media (min-width: 600px) {
    font-size: 80px;
  }
  
  @media (min-width: 900px) {
    font-size: 140px;
  }
  
  .animated {
    transition: all 400ms;
    position: absolute;
    transform: translate(-50%, -50%);
  }
  
  .slide-in {
    opacity: 0;
    transform: translate(-40%, -50%);
  }
  
  .slide-in-active {
    transition-delay: 150ms;
  }
  
  .slide-out {
    opacity: 1;
  }
  
  .slide-out-active {
    opacity: 0;
    transform: translate(-60%, -50%);
  }
}

.buttons {
  position: absolute;
  top: 10px;
  left: 10px;
}

button {
  padding: 10px;
  outline: none;
  border: none;
  -webkit-appearance: none;
  background: $primary;
  color: #fff;
  font-weight: bold;
  font-size: 18px;
  cursor: pointer;
  
  &:disabled {
    opacity: 0.2;
    cursor: no-drop;
  }
}
</style>
