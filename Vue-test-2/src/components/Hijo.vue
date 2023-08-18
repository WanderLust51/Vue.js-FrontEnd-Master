<script setup>
import { ref } from 'vue';

const props = defineProps([
    'contador'
])
console.log(props)


</script>

<template>
    <p>{{ contador }}</p>
</template>