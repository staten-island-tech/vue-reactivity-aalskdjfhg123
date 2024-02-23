<template>
    <div>
        <h2>{{ Destinations.power.value }} {{ Destinations.name }}s
            <button @click="Destinations.effect">Cost: {{ Destinations.price }} incrementals</button>
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
    color: black;
    background-color: white;
    border: solid black;
    transition: all 0.3s ease 0s;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 900;
/*     background: url(https://orteil.dashnet.org/cookieclicker/img/storeTile.jpg);
 */    background-position: 0px 128px;
}

button:hover {
    background-color: black;
    color: #fff;
}

button:active {
    background-color: rgb(92, 92, 92);
}
</style>