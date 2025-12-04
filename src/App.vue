<script setup>
	import Presupuesto from "./components/Presupuesto.vue";
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
				<Presupuesto />
			</div>
		</header>
	</div>
</template>