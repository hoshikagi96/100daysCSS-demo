<template>
  <div id="day">
    <h1>Day4</h1>

    <div class="frame">
      <div class="center">
        <div class="circle-1"></div>
        <div class="circle-2"></div>
        <div class="circle-3"></div>
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

$circle-shadow: 8px 8px 14px rgba(0, 0, 0, 0.31);
$bezier: cubic-bezier(0.12, 0.8, 0.43, 0.9);

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
  background-color: rgb(40, 154, 141);
  color: #333;
  font-family: 'Courier New', 'Courier', sans-serif;
}

.center {
  position: absolute;
  width: 100px;
  height: 100px;
  top: 150px;
  left: 150px;
}

.circle-1 {
  position: absolute;
  width: 90px;
  height: 90px;
  top: 5px;
  left: 5px;
  border-radius: 50%;
  background-color: #fff;
  box-shadow: $circle-shadow;
  animation: scaling-1 2s $bezier infinite alternate;
}

.circle-2 {
  position: absolute;
  width: 60px;
  height: 60px;
  top: 20px;
  left: 20px;
  border-radius: 50%;
  background-color: #fff;
  box-shadow: $circle-shadow;
  animation: scaling-2 2s $bezier infinite alternate;
}

.circle-3 {
  position: absolute;
  width: 30px;
  height: 30px;
  top: 35px;
  left: 35px;
  border-radius: 50%;
  background-color: #fff;
  box-shadow: $circle-shadow;
  animation: scaling-3 2s $bezier infinite alternate;
}

@keyframes scaling-1 {
  0% {
    transform: scale(0);
  }
  5% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes scaling-2 {
  0% {
    transform: scale(0);
  }
  40% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes scaling-3 {
  0% {
    transform: scale(0);
  }
  70% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}
</style>
