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
    <button @click ="autoUpgrade">autogen</button>
    <button @click="speed">speed</button>
    <h1>{{ tickSpeed }}</h1>
    <h1>{{ count }}</h1>
    <buildings v-for="things in penis" :key="things.name" :-destinations="things"/>

</div>
</template>


<script setup>
import { ref } from 'vue'
import buildings from '@/components/buildings.vue';


const upgrades = [
  {
    name: "upgrade1",
    price: 10,
   /*  effect: function(){
      upgradeClick()
    } */
  },
  {
    name: "upgrade2",
    price: 20
  },
  {
    name: "upgrade3",
    price: 30
  },
  {
    name: "upgrade4",
    price: 40
  },
] 
console.log(upgrades)

const count = ref(0)
 const clickUpgrade = ref(0)
 const clickMulti = ref(1)
const autoCount = ref(0)
const tickSpeed = ref(1000)

 function upgradeClick() {
  clickUpgrade.value++
} 

function multiClick() {
  clickMulti.value *= 2
}

function autoUpgrade(){
  autoCount.value++
}

function autoIncrement() {
  count.value += autoCount.value
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



const penis = [
        {
          name: "Venetian Renaissance",
          price: 1300,
          effect: function(){
            upgradeClick()
          }
        },
        {
          name: "Swiss Mountain Getaway",
          price: 800,
        },
        {
          name: "Ibizan Coastal Vacation",
          price: 1200,
        },
        {
          name: "Hawaiian Vacation",
          price: 900,
        },
        {
          name: "Cascade Mountains",
          price: 400,
        },
        {
          name: "Egyptian Exploration",
          price: 800,
        },
      ]
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