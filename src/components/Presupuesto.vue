<script setup>
	import { ref } from "vue";
	import Alerta from "./Alerta.vue";

	const inputPresupuesto = ref('');
    const mensajeError = ref('');
    

    const emit = defineEmits(['definir-presupuesto']);

	const añadirPresupuesto = () => {
		if (presupuesto.value <= 0 || isNaN(presupuesto.value)) {
            mensajeError.value = 'El presupuesto debe ser un número válido mayor que cero.';
			setTimeout(() => {
				mensajeError.value = '';
			}, 3000);
			return;
		}
        emit('definir-presupuesto', inputPresupuesto.value);
		// console.log("Presupuesto añadido:", presupuesto.value);
	};
</script>

<template>
	<form @submit.prevent="añadirPresupuesto">
		<Alerta v-if="mensajeError">
			<p class="text-center text-lg">
				<i class="pi pi-exclamation-circle mr-2"></i>
                {{ mensajeError }}
			</p>
		</Alerta>
		<div>
			<label
				for="presupuesto"
				class="block text-gray-700 text-xl mb-4 text-center"
				>Definir Presupuesto</label
			>
			<input
				id="presupuesto"
				type="number"
				class="w-full p-4 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent text-center text-xl"
				placeholder="Añade tu presupuesto"
				v-model.number="inputPresupuesto"
			/>
		</div>

		<input
			type="submit"
			value="Añadir"
			class="mt-4 bg-blue-500 text-white p-2 rounded-md hover:bg-blue-600 cursor-pointer w-full shadow-md transition-colors duration-300 ease-in-out"
		/>
	</form>
</template>
