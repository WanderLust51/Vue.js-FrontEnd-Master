<script setup>
	import { ref } from 'vue'
	function saludar(event){
		console.log(event)
	}

	function uncopy(e){
		if(e.ctrlKey && e.key == 'c'){
			alert('sin copiar chamo')
			e.preventDefault()
		}
	}

	let yea = ref('')

</script>

<template>

	<header>
		<img src="https://img.pokemondb.net/design/avif/header-lg.avif" alt="">
		<nav @click.stop="console.log('Demonios')">
			<div @click="saludar($event)">Pókemon data</div>
			<div>Game mechanics</div>
			<div>Pókemon games</div>
			<div>Community/Other</div>
			<div><form action=""><input type="text" @keydown="uncopy($event)" v-model="yea"><input type="submit" value=" " @click.prevent=""></form></div>
		</nav>
	</header>
	<br><br>
	<input type="text" @keypress="saludar($event)">
	<h1>{{ yea }}</h1>


</template>

<style scoped>

</style>
