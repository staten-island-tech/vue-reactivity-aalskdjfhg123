<template>
    <div>
    <h2>{{ Destinations.name }}</h2>
    <h2> {{ Destinations.price }}</h2>
    <h3>{{ Destinations.power.value }}</h3>
    <button @click="Destinations.effect">upgrade</button>
    </div>
</template>



<script setup>
import { ref } from 'vue';

const props = defineProps({
    Destinations: Object,
}) //if i change it from destinations to something else the code get very angry



</script>



<style scoped>

</style>