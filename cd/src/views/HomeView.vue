<template>
  <div>
    <button @click="upgradeClick"> upgrade</button>
    <h1>{{ clickUpgrade }}</h1>

    <button @click="multiClick"> mult</button>
    <h1>{{ clickMulti }}</h1>

    <img src="https://th.bing.com/th/id/R.ee9ad5f805f79dd1a32db3221b4ea5ed?rik=DzBLh1BSTRI35Q&pid=ImgRaw&r=0" alt=""
      @click="increment" class="clicker">
      <h1>{{ 1 * clickMulti + clickUpgrade }}</h1>
      <button @click="upgradeClick">upgrade</button>
    <button>autogen</button>
    <button @click="speed">speed</button>
    <h1>{{ tickSpeed }}</h1>
    <h1>{{ displayCount }}</h1>
  </div>
</template>


<script setup>
import { ref } from 'vue'

const count = ref(0)
const clickUpgrade = ref(0)
const clickMulti = ref(1)
const autoCount = ref(1)
const displayCount = count
const tickSpeed = ref(1000)

function upgradeClick() {
  clickUpgrade.value++
}

function multiClick() {
  clickMulti.value *= 2
}

function autoIncrement() {
  count.value += autoCount.value
  console.log(tickSpeed)
}
function speed() {
  tickSpeed.value *= .5;
  clearInterval(interval);
  interval = setInterval(autoIncrement, tickSpeed.value);
}

let interval = setInterval(autoIncrement, tickSpeed.value);

function increment() {
  count.value += 1 * clickMulti.value + clickUpgrade.value
}


</script>




<style lang="scss" scoped>
.clicker {
  width: 30%;
  height: 30%;
}

.clicker:hover {
  transform: scale(1.02);
}

.clicker:active {
  transform: scale(.98);
}
</style>