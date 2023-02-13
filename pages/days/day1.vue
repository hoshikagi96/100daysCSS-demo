<template>
  <div>
    <h1>Day1</h1>

    <div class="frame">
      <div class="center">
        <div class="text-100">
          <p class="dummy-100">100</p>
          <div class="one-1"></div>
          <div class="one-2"></div>
          <div class="zero-1"></div>
          <div class="zero-2"></div>
        </div>
        <span class="text-days">DAYS</span>
        <span class="text-sub">CSS CHALLENGE</span>
      </div>
    </div>

    <footer><NuxtLink to="/">Back to HOME</NuxtLink></footer>
  </div>
</template>

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
  background: rgb(141, 45, 194);
  background: linear-gradient(
    60deg,
    rgba(141, 45, 194, 1) 0%,
    rgba(209, 85, 150, 1) 56%,
    rgba(208, 94, 69, 1) 100%
  );
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

.text-100 {
  position: relative;
  width: 200px;
  height: 100px;

  .dummy-100 {
    visibility: hidden;
  }
  div {
    position: absolute;
    content: '';
    box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.21);
  }
  .one-1 {
    z-index: -1;
    width: 20px;
    height: 40px;
    border-radius: 3px;
    background-color: white;
    top: 0px;
    left: -16px;
    transform: rotate(50deg);
  }
  .one-2 {
    z-index: 2;
    width: 24px;
    height: 100px;
    border-radius: 3px;
    background-color: white;
    top: 0px;
    left: 0px;
  }
  .zero-1 {
    z-index: 1;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background-color: transparent;
    border: 24px solid white;
    top: 0px;
    left: 17px;
  }
  .zero-2 {
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background-color: transparent;
    border: 24px solid white;
    top: 0px;
    left: 100px;
  }
}
.text-days {
  font-size: 82px;
  font-weight: 700;
  line-height: 60px;
  margin-top: 6px;
}
.text-sub {
  font-size: 24px;
  font-weight: 700;
  line-height: 20px;
}
</style>
