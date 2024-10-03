<template>
  <h1>Time:</h1>
</template>

<script>
import { onBeforeMount, onBeforeUnmount, onBeforeUpdate, onMounted, onUpdated, ref } from 'vue';

const time = ref(0);
let timerId;

const props = defineProps({
    inputValue: {
        type: String,
        default: "Nguyen Van A",
    }
});

// Giai doan mounting
onBeforeMount(() =>{
    console.log("Component before mount");    
});

onMounted(() => {
    setInterval(() => {
        time.value++;
    }, 1000);
    console.log("Component mounted");
});

// Giai doan updating
onBeforeUpdate(() => {
    console.log("Component before update");
});

onUpdated(() => {
   console.log("Component before unmount");
});

// Giai doan unmount
onBeforeUnmount(() =>{
   console.log("Component before unmount");
   clearInterval(timerId);
});

</script>

<style>

</style>