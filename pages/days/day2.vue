<template>
  <div id="day2">
    <h1>Day2</h1>

    <div class="frame">
      <div class="center">
        <div id="menu-button" class="menu-button" @click="toggleActive">
          <div class="bar bar-1"></div>
          <div class="bar bar-2"></div>
          <div class="bar bar-3"></div>
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
  methods: {
    toggleActive() {
      const button = document.getElementById('menu-button')
      button.classList.toggle('active')
    },
  },
})
</script>

<style lang="scss" scoped>
// delete the following line if no text is used
// edit the line if you wanna use other fonts
@import url(https://fonts.googleapis.com/css?family=Open+Sans:700,300);

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
  background: rgb(108, 134, 164);
  color: #333;
  font-family: 'Courier New', 'Courier', sans-serif;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
}

$cubic-bezier-in: cubic-bezier(0.3, 1, 0.7, 1);

.menu-button {
  width: 80px;
  height: 80px;
  cursor: pointer;
  .bar {
    display: block;
    position: absolute;
    box-sizing: border-box;
    height: 8px;
    width: 80px;
    border-radius: 8px;
    background-color: white;
    box-shadow: 2px 0 10px rgba(0, 0, 0, 0.327);
    transition: background-color 0.2s ease-in-out;
    &.bar-1 {
      top: 16px;
      animation: animate-bar-1-rev 0.7s ease-in-out forwards;
    }
    &.bar-2 {
      top: 36px;
      animation: animate-bar-2-rev 0.7s ease-in-out forwards;
    }
    &.bar-3 {
      top: 56px;
      animation: animate-bar-3-rev 0.7s ease-in-out forwards;
    }
  }
  &.active {
    .bar {
      &.bar-1 {
        animation: animate-bar-1 0.7s $cubic-bezier-in forwards;
      }
      &.bar-2 {
        animation: animate-bar-2 0.7s $cubic-bezier-in forwards;
      }
      &.bar-3 {
        animation: animate-bar-3 0.7s $cubic-bezier-in forwards;
      }
    }
  }
}

@keyframes animate-bar-1 {
  0% {
    transform: translate3d(0, 0, 0);
  }
  50% {
    transform: translateY(20px);
  }
  100% {
    transform: translateY(20px) rotate(45deg);
  }
}

@keyframes animate-bar-2 {
  0% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: scale(0);
  }
}

@keyframes animate-bar-3 {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(-20px) rotate(135deg);
  }
}

@keyframes animate-bar-1-rev {
  0% {
    transform: translateY(20px) rotate(45deg);
  }
  50% {
    transform: translateY(20px);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes animate-bar-2-rev {
  0% {
    opacity: 0;
    transform: scale(0);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes animate-bar-3-rev {
  0% {
    transform: translateY(-20px) rotate(135deg);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0);
  }
}
</style>
