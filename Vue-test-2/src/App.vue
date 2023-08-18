<script setup>
	import { ref, computed } from 'vue'
	import { watchEffect } from 'vue';
    import { onMounted } from 'vue';

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

	let data = ref()

	//watch effect
	watchEffect(async () => {
  		const response = await fetch(`https://jsonplaceholder.typicode.com/users/`)
			.then(response=>response.json())
		data.value = await response
	}) 

	//Variables computadas
	let cantidad = ref(15);
	let precio = ref(6);
	let subtotal = computed(function(){
		return cantidad.value * precio.value
	})

	//Usando componentes
	import  Productos  from './components/productos.vue'
	import Hijo from './components/hijo.vue'

	let contador = ref(5)


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

	<!-- USANDO V-FOR -->
	<ul>
		<li v-for="(item, index) in data" :key="index">
			{{ index }} - {{ item.name }}
		</li>
	</ul>

	<h1>Subtotal {{ subtotal }}</h1>
	
	<!-- Usando componentes -->
	<Productos />
	<Hijo :contador="900" />

</template>

<style scoped>

</style>
