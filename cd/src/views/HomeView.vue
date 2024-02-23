<template>
  <div class="body">

    <div class="countContainer"><span class="count">{{ count }} incrementals</span></div>
    <div class="tickspeed">
      <div class="button"> <button @click="tick">Upgrade tickSpeed cost: {{ tickSpeed.price.value }}</button>
        <div class="tickDisplay">{{ Math.round(tickSpeed.speed.value) / 1000 }} seconds per tick</div>
      </div>
    </div>
    <buildings v-for="things in upgrades" :key="things.name" :-destinations="things" />
  </div>
</template>


<script setup>
import { ref } from 'vue'
import buildings from '@/components/buildings.vue';

const count = ref(10)

let upgrades = {
  upgrade1: {
    name: "incremental incrementer",
    price: ref(10),
    power: ref(0),
    effect: function () {
      if (count.value >= this.price.value) {
        this.power.value++
        count.value -= this.price.value
        this.price.value = Math.round(this.price.value *= 1.15)
      } else {
      }
    },
  },
  upgrade2: {
    name: "incremental incrementer incrementer",
    price: ref(100),
    power: ref(0),
    effect: function () {
      if (count.value >= this.price.value) {
        this.power.value++
        count.value -= this.price.value
        this.price.value = Math.round(this.price.value *= 1.15)
      } else {
        alert("poor")
      }
    },
  },
  upgrade3: {
    name: "incremental incrementer incrementer incrementer",
    price: ref(10000),
    power: ref(0),
    effect: function () {
      if (count.value >= this.price.value) {
        this.power.value++
        count.value -= this.price.value
        this.price.value = Math.round(this.price.value *= 1.15)
      } else {
        alert("poor")
      }
    }
  },
  upgrade4: {
    name: "incremental incrementer incrementer incrementer incrementer",
    price: ref(1000000),
    power: ref(0),
    effect: function () {
      if (count.value >= this.price.value) {
        this.power.value++
        count.value -= this.price.value
        this.price.value = Math.round(this.price.value *= 1.15)
      } else {
        alert("poor")
      }
    }
  },
}


const tickSpeed = {
  speed: ref(1000),
  price: ref(1000),
  effect: function () {
    this.speed.value *= .875
    this.price.value = Math.round(this.price.value *= 10)
  }
}



function makeGen(maker, makee) {
  makee.power.value += maker.power.value
}

function autoIncrement() {
  count.value += upgrades.upgrade1.power.value
}
function tick() {
  if (count.value >= tickSpeed.price.value) {
    count.value -= tickSpeed.price.value
    tickSpeed.effect()
    clearInterval(interval);
    clearInterval(interval1)
    clearInterval(interval2)
    clearInterval(interval3) //removes old tickspeed so the new and old dont stack
    interval = setInterval(autoIncrement, tickSpeed.speed.value);//new tickspeed
    interval1 = setInterval(makeGen, tickSpeed.speed.value, upgrades.upgrade2, upgrades.upgrade1);
    interval2 = setInterval(makeGen, tickSpeed.speed.value, upgrades.upgrade3, upgrades.upgrade2);
    interval3 = setInterval(makeGen, tickSpeed.speed.value, upgrades.upgrade4, upgrades.upgrade3);
  }
}
let interval = setInterval(autoIncrement, tickSpeed.speed.value);
let interval1 = setInterval(makeGen, tickSpeed.speed.value, upgrades.upgrade2, upgrades.upgrade1);
let interval2 = setInterval(makeGen, tickSpeed.speed.value, upgrades.upgrade3, upgrades.upgrade2);
let interval3 = setInterval(makeGen, tickSpeed.speed.value, upgrades.upgrade4, upgrades.upgrade3);
//there is 1000% a better way to do this, i am just not smart enough to knpw

</script>






<style lang="scss" scoped>
.tickDisplay {
  font-size: 35px;
  margin-left: 43vw;
  margin-top: 2.5vh;
  margin-bottom: 4vh;
}

button {
  position: relative;
  margin-top: 5vh;
  margin-left: 40vw;
  padding: 1.3em 3em;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 2.5px;
  color: #000;
  background-color: #fff;
  border: solid black;
  transition: all 0.3s ease 0s;
  border-radius: 10px;
  cursor: pointer;
  font-weight: 900;
}

button:hover {
  background-color: black;
  color: #fff;
}

button:active {
  background-color: rgb(92, 92, 92);
}

.countContainer {
  display: flex;
  font-size: 80px;
  align-items: center;
  justify-content: center;
  margin-top: 5vh;
}
</style>