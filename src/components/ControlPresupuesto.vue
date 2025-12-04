<script setup>
	import grafico from "../assets/img/grafico.jpg";

	const props = defineProps({
		presupuesto: {
			type: Number,
			required: true,
		},
		gastos: {
			type: Array,
			required: true,
		},
		disponible: {
			type: Number,
			required: true,
		},
		totalGastos: {
			type: Number,
			required: true,
		},
	});

    const emit = defineEmits(['resetear-app']);
</script>

<template>
	<div class="flex flex-col gap-6">
		<div
			class="flex flex-col md:flex-row items-center justify-around gap-6"
		>
			<div id="contenedorGrafica">
				<img :src="grafico" alt="Gráfica de gastos vs presupuesto" />
			</div>
			<div
				id="contenedorPresupuesto"
				class="flex flex-col gap-4 items-start"
			>
				<p class="text-xl text-gray-700">
					Presupuesto: $ {{ presupuesto }}
				</p>
				<p class="text-xl text-gray-700">
					Total Gastos: $ {{ totalGastos }}
				</p>
				<p class="text-xl text-gray-700">
					Disponible: $ {{ disponible }}
				</p>
			</div>
		</div>
		<div class="flex justify-center">
			<button
                @click="emit('resetear-app')"
				class="bg-red-500 text-white px-4 py-2 rounded-lg shadow-lg hover:bg-red-600 transition-colors duration-300 cursor-pointer"
			>
				Resetear
			</button>
		</div>
	</div>
</template>
