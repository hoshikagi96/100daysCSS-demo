<template>
  <div id="day">
    <h1>Day5</h1>

    <div class="frame">
      <div class="center">
        <div class="info-container">
          <div class="info-header">
            <div class="text-left">
              <p class="title">WEEKLY REPORT</p>
              <p class="duration">01.Feb-07.Feb</p>
            </div>
            <div class="text-right">
              <p class="label">Revenue</p>
              <p class="revenue">${{ revenue }}</p>
            </div>
          </div>
          <div class="info-content">
            <div class="items-label">
              <span class="views">Views</span>
              <span class="purchases">Purchases</span>
            </div>
            <div class="graph-container">
              <div class="line top"></div>
              <div class="line middle"></div>
              <div class="line bottom"></div>
              <div class="views-graph">
                <svg>
                  <polyline class="line-view" :points="viewsPoints"></polyline>
                </svg>
                <div class="points view">
                  <div :style="getPointPos('view', 0)"></div>
                  <div :style="getPointPos('view', 1)"></div>
                  <div :style="getPointPos('view', 2)"></div>
                  <div :style="getPointPos('view', 3)"></div>
                  <div :style="getPointPos('view', 4)"></div>
                  <div :style="getPointPos('view', 5)"></div>
                  <div :style="getPointPos('view', 6)"></div>
                </div>
              </div>
              <div class="purchases-graph">
                <svg>
                  <polyline
                    class="line-purchase"
                    :points="purchasesPoints"
                  ></polyline>
                </svg>
                <div class="points purchase">
                  <div :style="getPointPos('purchase', 0)"></div>
                  <div :style="getPointPos('purchase', 1)"></div>
                  <div :style="getPointPos('purchase', 2)"></div>
                  <div :style="getPointPos('purchase', 3)"></div>
                  <div :style="getPointPos('purchase', 4)"></div>
                  <div :style="getPointPos('purchase', 5)"></div>
                  <div :style="getPointPos('purchase', 6)"></div>
                </div>
              </div>
              <div class="days">
                <span>MON</span>
                <span>TUE</span>
                <span>WED</span>
                <span>THU</span>
                <span>FRI</span>
                <span>SAT</span>
                <span>SUN</span>
              </div>
            </div>
          </div>
        </div>
        <div class="input-container">
          <div>
            <label for="views-num">Views</label>
            <input
              id="views-num"
              v-model="inputViews"
              placeholder="Separated by ',' (max: 1000)"
              type="text"
            />
          </div>
          <div>
            <label for="views-num">Purchases</label>
            <input
              id="purchases-num"
              v-model="inputPurchases"
              placeholder="Separated by ',' (max: 100)"
              type="text"
            />
          </div>
          <button @click="applyInputNums()">apply</button>
        </div>
      </div>
    </div>

    <footer><NuxtLink to="/">Back to HOME</NuxtLink></footer>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import { onMounted } from 'vue'

const MAX_VIEW = 1000
const MAX_PURCHASE = 100
const POINTS_X = [10, 51, 91, 131, 171, 211, 251]
const revenue = 3621.79
const views = ref([458, 812, 746, 877, 517, 434, 458])
const purchases = ref([26, 41, 90, 36, 25, 62, 20])
const inputViews = ref('458, 812, 746, 877, 517, 434, 458')
const inputPurchases = ref('26, 41, 90, 36, 25, 62, 20')

onMounted(() => {})

const viewsPoints = computed(() => {
  const pointsList = []
  for (let i = 0; i < 7; i++) {
    const pointY = getPointY('view', i)
    pointsList.push(`${POINTS_X[i]},${pointY}`)
  }
  return pointsList.join(' ')
})

const purchasesPoints = computed(() => {
  const pointsList = []
  for (let i = 0; i < 7; i++) {
    const pointY = getPointY('purchase', i)
    pointsList.push(`${POINTS_X[i]},${pointY}`)
  }
  return pointsList.join(' ')
})

const getPointY = (itemName, id) => {
  if (itemName === 'view') {
    return ((MAX_VIEW - views.value[id]) / MAX_VIEW) * 80
  } else if (itemName === 'purchase') {
    return ((MAX_PURCHASE - purchases.value[id]) / MAX_PURCHASE) * 80
  }
}

const getPointPos = (itemName, id) => {
  const leftPos = POINTS_X[id] - 2
  const topPos = getPointY(itemName, id) - 2
  return `left: ${leftPos}px; top: ${topPos}px;`
}

const applyInputNums = () => {
  views.value = inputViews.value.split(',').map((n) => Number(n))
  purchases.value = inputPurchases.value.split(',').map((n) => Number(n))
  console.log(views.value)
  console.log(purchases.value)
}
</script>

<style lang="scss" scoped>
// delete the following line if no text is used
// edit the line if you wanna use other fonts
@import url(https://fonts.googleapis.com/css?family=Open+Sans:700,300);
$yellow: rgb(233, 180, 88);
$green: rgb(87, 191, 113);

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
  background-color: rgb(252, 160, 175);
  color: #333;
  font-family: 'Open Sans', Helvetica, sans-serif;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.info-container {
  width: 280px;
  height: 220px;
  border-radius: 4px;
  overflow: hidden;
  background-color: white;
  display: flex;
  flex-direction: column;
  box-shadow: 10px 10px 14px rgba(0, 0, 0, 0.242);
}

.info-header {
  width: auto;
  min-height: 60px;
  background-color: rgb(67, 67, 152);
  display: flex;
  flex-direction: row;
  color: #fff;
  font-size: 11px;
  align-items: center;
  justify-content: space-between;
  padding: 0px 16px;
  .text-left {
    display: flex;
    flex-direction: column;
    p.title {
      font-weight: bold;
      font-size: 14px;
    }
  }
  .text-right {
    display: flex;
    flex-direction: column;
    align-items: end;
    p.revenue {
      font-weight: bold;
      font-size: 14px;
    }
  }
  p {
    display: block;
    margin: 0;
  }
}

.info-content {
  padding: 0px 10px;
  position: relative;
  .items-label {
    height: 40px;
    width: auto;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: end;
    span {
      font-size: 9px;
      &.views::before {
        content: '';
        display: inline-block;
        width: 10px;
        height: 3px;
        border-radius: 2px;
        background-color: $yellow;
        margin: 0px 6px 2px 16px;
      }
      &.purchases::before {
        content: '';
        display: inline-block;
        width: 10px;
        height: 3px;
        border-radius: 2px;
        background-color: $green;
        margin: 0px 6px 2px 16px;
      }
    }
  }

  .graph-container {
    width: auto;
    height: 120px;
    position: relative;
    overflow: hidden;
    .views-graph {
      position: absolute;
      width: 100%;
      height: 100%;
      z-index: 2;
    }
    .purchase-graph {
      position: absolute;
      width: 100%;
      height: 100%;
      z-index: 3;
    }
    .line {
      position: absolute;
      width: 100%;
      height: 40px;
      top: 0px;
      border-top: 1px solid rgb(233, 233, 233);
      z-index: 1;
      &.top {
        top: 0px;
      }
      &.middle {
        top: 40px;
      }
      &.bottom {
        top: 80px;
      }
    }
    polyline {
      fill: transparent;
      stroke-width: 2px;
      transition: 1s;
      &.line-view {
        stroke: $yellow;
      }
      &.line-purchase {
        stroke: $green;
      }
    }
    .points {
      position: absolute;
      top: 0;
      left: 0;
    }
    .points div {
      position: absolute;
      top: 0;
      left: 0%;
      width: 4px;
      height: 4px;
      border-radius: 50%;
      background-color: black;
    }
    .points.view div {
      position: absolute;
      background-color: $yellow;
    }
    .points.purchase div {
      position: absolute;
      background-color: $green;
    }
    .days {
      position: absolute;
      top: 80px;
      width: 100%;
      height: 36px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      color: #b7b7b7;
      font-size: 9px;
      font-weight: bold;
    }
  }
}
.input-container {
  padding-top: 10px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    label {
      line-height: 14px;
      font-size: 12px;
      font-weight: bold;
      color: rgb(86, 86, 86);
    }
    input {
      width: 200px;
    }
  }
  button {
    background-color: rgb(6, 179, 142);
    height: 24px;
    border: none;
    border-radius: 4px;
    color: #fff;
    cursor: pointer;
    font-weight: bold;
    box-shadow: 10px 10px 14px rgba(0, 0, 0, 0.242);
    &:hover {
      background-color: rgb(25, 209, 169);
    }
  }
}
</style>
