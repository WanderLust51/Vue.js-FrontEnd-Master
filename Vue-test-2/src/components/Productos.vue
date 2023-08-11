<script setup>
    import { ref, onMounted, onUpdated } from 'vue';

    let mounting = ref(5)

    onMounted(function(){
        setInterval(function(){
            mounting.value += 5;
        },5000)
    })
    onUpdated(function(){
        console.log(mounting.value)
    })

</script>

<template>
    
    <p>{{ mounting }}</p>
</template>