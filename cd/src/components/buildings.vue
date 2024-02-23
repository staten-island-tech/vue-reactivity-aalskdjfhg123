<template>
    <div>
        <h2>{{ Destinations.power.value }} {{ Destinations.name }}s
            <button @click="Destinations.effect">{{ Destinations.price }} cookie clickers clikers</button>
        </h2>

    </div>
</template>



<script setup>
import { ref } from 'vue';

const props = defineProps({
    Destinations: Object,
}) //if i change it from destinations to something else the code get very angry



</script>



<style scoped>


h2 {
    font-weight: 900;
    letter-spacing: 2.5px;
    margin-bottom: 50px;
    position: relative;
    left: 3vw;
}

button {
    position: absolute;
    left: 60vw;
    padding: 10px;
    width: 30vw;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 2.5px;
    color: white;
    background-color: #84816e;
    border: solid #5d5c4a;
    transition: all 0.3s ease 0s;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 900;
/*     background: url(https://orteil.dashnet.org/cookieclicker/img/storeTile.jpg);
 */    background-position: 0px 128px;
}

button:hover {
    background-color: #cac5b7;
    color: #fff;
}

button:active {
    background-color: rgb(92, 92, 92);
}
</style>