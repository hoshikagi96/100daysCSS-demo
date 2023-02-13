<template>
  <div id="day3">
    <h1>Day3</h1>

    <div class="frame">
      <div class="center">
        <div class="cover"></div>
        <div class="circle">
          <div class="sky"></div>
          <div class="sun"></div>
          <div class="mountain">
            <div class="mountain-left"></div>
            <div class="mountain-right"></div>
          </div>
          <div class="shadow"></div>
          <div class="ground"></div>
        </div>
      </div>
    </div>

    <footer><NuxtLink to="/">Back to HOME</NuxtLink></footer>
  </div>
</template>

<script>
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {}
  },
  methods: {},
})
</script>

<style lang="scss" scoped>
// delete the following line if no text is used
// edit the line if you wanna use other fonts
@import url(https://fonts.googleapis.com/css?family=Open+Sans:700,300);
$back-color: rgb(37, 37, 50);

// use only the available space inside the 400x400 frame
.frame {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 400px;
  height: 400px;
  margin-top: -200px;
  margin-left: -200px;
  border-radius: 2px;
  box-shadow: 4px 8px 16px 0 rgba(0, 0, 0, 0.1);
  overflow: hidden;
  background-color: $back-color;
  color: #333;
  font-family: 'Courier New', 'Courier', sans-serif;
}

.center {
  position: relative;
}

.circle {
  position: absolute;
  transform: translate(110px, 110px);
  overflow: hidden;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  clip-path: circle(90px at 90px 90px);
}

.cover {
  position: absolute;
  transform: translate(100px, 100px);
  z-index: 1;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background-color: transparent;
  animation: blackout 4s infinite;
}

.sky {
  position: absolute;
  z-index: 0;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background-color: skyblue;
}

.sun {
  position: absolute;
  top: 24px;
  left: 20px;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  background-color: rgb(255, 217, 0);
  transform-origin: 70px 110px;
  animation: sun-rotation 4s ease-in-out infinite;
}

.mountain {
  .mountain-left {
    position: absolute;
    width: 120px;
    height: 60px;
    top: 70px;
    left: 30px;
    background: darken(white, 10%);
    clip-path: polygon(0% 100%, 100% 100%, 50% 0%);
    animation: lighting-left 4s ease-in-out infinite;
  }
  .mountain-right {
    z-index: 1;
    position: absolute;
    width: 60px;
    height: 60px;
    top: 70px;
    left: 90px;
    clip-path: polygon(30% 100%, 100% 100%, 0% 0%);
    animation: lighting-right 4s ease-in-out infinite;
  }
}

.shadow {
  z-index: 2;
  position: absolute;
  width: 280px;
  height: 30px;
  background: rgba(99, 99, 99, 0.462);
  top: 130px;
  left: -50px;
  clip-path: polygon(80px 0%, 100% 100%, 200px 0%);
  animation: moving-shadow 4s linear infinite;
}

.ground {
  position: absolute;
  height: 100px;
  width: 200px;
  top: 130px;
  background-color: rgb(227, 215, 129);
}

@keyframes blackout {
  0% {
    background-color: $back-color;
  }
  20% {
    background-color: transparent;
  }
  75% {
    background-color: transparent;
  }
  100% {
    background-color: $back-color;
  }
}

@keyframes sun-rotation {
  0% {
    transform: rotate(-30deg);
  }
  25% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(130deg);
  }
}

@keyframes lighting-left {
  0% {
    background: darken(white, 20%);
  }
  25% {
    background: darken(white, 0%);
  }
  40% {
    background: darken(white, 0%);
  }
  80% {
    background: darken(white, 20%);
  }
  100% {
    background: darken(white, 30%);
  }
}

@keyframes lighting-right {
  0% {
    background: darken(white, 30%);
  }
  25% {
    background: darken(white, 10%);
  }
  45% {
    background: darken(white, 10%);
  }
  80% {
    background: darken(white, 0%);
  }
  100% {
    background: darken(white, 10%);
  }
}

@keyframes moving-shadow {
  0% {
    clip-path: polygon(80px 0%, 100% 30%, 200px 0%);
  }
  25% {
    clip-path: polygon(80px 0%, 90% 60%, 200px 0%);
  }
  34% {
    clip-path: polygon(80px 0%, 90% 60%, 200px 0%);
  }
  50% {
    clip-path: polygon(80px 0%, 60% 40%, 200px 0%);
  }
  75% {
    clip-path: polygon(80px 0%, 30% 50%, 200px 0%);
  }
  82% {
    clip-path: polygon(80px 0%, 15% 60%, 200px 0%);
  }
  100% {
    clip-path: polygon(80px 0%, 0% 30%, 200px 0%);
  }
}
</style>
