<template>
    <div>
    <h2>{{ Destinations.name }}</h2>
    <h2> {{ Destinations.price }}</h2>
    <button @click="Destinations.effect">upgrade</button>
    </div>
</template>



<script setup>
import { ref } from 'vue';

const props = defineProps({
    Destinations: Object,
})


</script>



<style scoped>

</style>