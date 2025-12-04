<script setup>
	import Presupuesto from "./components/Presupuesto.vue";
	import ControlPresupuesto from "./components/ControlPresupuesto.vue";
	import { ref, computed } from "vue";

	const presupuesto = ref(0);
	const gastos = ref([
		{ id: 1, nombre: "Comida", cantidad: 100 },
		{ id: 2, nombre: "Transporte", cantidad: 200 },
		{ id: 3, nombre: "Entretenimiento", cantidad: 50 }
	]);


	const definirPresupuesto = (cantidad) => {
		presupuesto.value = cantidad;
		console.log("Presupuesto definido en App.vue:", presupuesto.value);
	};

	const resetearApp = () => {
		presupuesto.value = 0;
		gastos.value = [];
	};

	const totalGastos = computed(() => {
		return gastos.value.reduce((total, gasto) => total + gasto.cantidad, 0);
	})

	const disponible = computed(() => {
		return presupuesto.value - totalGastos.value;
	});


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
					<ControlPresupuesto
						:presupuesto="presupuesto"
						:gastos="gastos"
						:disponible="disponible"
						:total-gastos="totalGastos"
						@resetear-app="resetearApp"
					/>
				</div>
			</div>
		</header>
	</div>
</template>
