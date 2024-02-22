<template>
  <div>
    <button @click="upgradeClick"> upgrade</button>
    <h1>{{ clickUpgrade }}</h1>
    <!-- 
    <button @click="multiClick"> mult</button>
    <h1>{{ clickMulti }}</h1> -->

    <img src="https://th.bing.com/th/id/R.ee9ad5f805f79dd1a32db3221b4ea5ed?rik=DzBLh1BSTRI35Q&pid=ImgRaw&r=0" alt=""
      @click="increment" class="clicker">
    <h1>{{ 1 /* * clickMulti */ + clickUpgrade }}</h1>
    <button @click="upgradeClick">upgrade</button>
    <button @click="tick">speed</button>
    <h1>{{ tickSpeed }}</h1>
    <h1>{{ count }}</h1>
    <buildings v-for="things in upgrades" :key="things.name" :-destinations="things" />

  </div>
</template>


<script setup>
import { ref } from 'vue'
import buildings from '@/components/buildings.vue';

let upgrades = {
  upgrade1: {
    price: 100,
    power: ref(1),
    effect: function () {
      this.power.value++
    }
  },
  upgrade2: {
    price: 200,
    power: ref(0),
    effect: function () {
      this.power.value++
    }
  },
  upgrade3: {
    price: 300,
    power: ref(0),
    effect: function () {
      this.power.value++
    }
  },
  upgrade4: {
    price: 400,
    power: ref(0),
    effect: function () {
      this.power.value++
    }
  },
}


const count = ref(0)
const clickUpgrade = ref(0)
/* const clickMulti = ref(1)
 */
const tickSpeed = ref(1000)


function makeGen(maker, makee) {
  makee.power.value += maker.power.value
}

function upgradeClick() {
  clickUpgrade.value++
}

/* function multiClick() {
  clickMulti.value *= 2
}
 */

function autoIncrement() {
  count.value += upgrades.upgrade1.power.value
}
function tick() {
  tickSpeed.value *= .95;
  clearInterval(interval, interval);//removes old tickspeed so the new and old dont stack
  interval = setInterval(autoIncrement, tickSpeed.value);//new tickspeed
  interval1 = setInterval(makeGen, tickSpeed.value, upgrades.upgrade2, upgrades.upgrade1);
  interval2 = setInterval(makeGen, tickSpeed.value, upgrades.upgrade3, upgrades.upgrade2);
  interval3 = setInterval(makeGen, tickSpeed.value, upgrades.upgrade4, upgrades.upgrade3);
}
let interval = setInterval(autoIncrement, tickSpeed.value);
let interval1 = setInterval(makeGen, tickSpeed.value, upgrades.upgrade2, upgrades.upgrade1);
let interval2 = setInterval(makeGen, tickSpeed.value, upgrades.upgrade3, upgrades.upgrade2);
let interval3 = setInterval(makeGen, tickSpeed.value, upgrades.upgrade4, upgrades.upgrade3);
//there is 1000% a better way to do this, i am just not smart enough to knpw

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