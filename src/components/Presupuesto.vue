<script setup></script>

<template>
    <form>
        <div>
            <label for="presupuesto" class="block text-gray-700 text-xl mb-4 text-center">Definir Presupuesto</label>
            <input 
                id="presupuesto"
                type="number"
                class="w-full p-4 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent text-center text-xl"
                placeholder="Añade tu presupuesto"
            />
        </div>

        <input type="submit" value="Añadir" class="mt-4 bg-blue-500 text-white p-2 rounded-md hover:bg-blue-600 cursor-pointer w-full shadow-md transition-colors duration-300 ease-in-out" />
    </form>
</template>