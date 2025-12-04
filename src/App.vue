<script setup>
	import Presupuesto from "./components/Presupuesto.vue";
	import { ref } from "vue";

	const presupuesto = ref(0);

	const definirPresupuesto = (cantidad) => {
		presupuesto.value = cantidad;
		console.log("Presupuesto definido en App.vue:", presupuesto.value);
	}
</script>

<template>
	<div class="mx-auto">
		<header class="bg-blue-500 px-10">
			<h1 class="pt-8 text-white text-center text-4xl font-bold">
				Planificador de Gastos
			</h1>
			<div
				class="mx-auto max-w-3xl transform translate-y-14 p-14 bg-white shadow-lg rounded-lg"
			>
				<Presupuesto 
					v-if="presupuesto === 0"
					@definir-presupuesto="definirPresupuesto" 
				/>
				<div v-else class="text-center">
					<h2 class="text-2xl font-semibold mb-4">Presupuesto Definido:</h2>
					<p class="text-3xl text-gray-700">$ {{ presupuesto }}</p>
				</div>
			</div>
		</header>
	</div>
</template>