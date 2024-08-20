<template>
    <h1 class="title-gym">BULL'S GYM</h1>
    <main class="w-full h-auto ml-2">
        <section>
            <div class="mx-auto p-4">
                <div class="bg-gray-900 dark:bg-gray-700 shadow rounded-lg p-6">
                    <h1 class="text-xl font-semibold mb-4 text-gray-100 dark:text-gray-100">Crear nueva evaluación de servicio</h1>
                    <p class="text-gray-100 dark:text-gray-100 mb-6">Ingresa la información correspondiente para crear una nueva evaluación de servicio.</p>
                    <form>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
                            <input type="number" placeholder="ID del Usuario" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                            <select class="rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                                <option value="">Servicios</option>
                                <option value="SNutricion">Servicios de nutrición</option>
                                <option value="HP">Horarios y precios</option>
                                <option value="C">Comunidad</option>
                                <option value="PE">Programas de entretenimiento</option>
                            </select>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
                            <input type="text" placeholder="Calificación" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                            <input type="text" placeholder="Comentario" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                            <div class="flex items-center mb-6">
                                <input type="checkbox" id="estatus" class="mr-2">
                                <label for="estatus" class="text-gray-100 dark:text-gray-100">Estatus (Activo/Inactivo)</label>
                            </div>
                        </div>
                        <input type="datetime-local" placeholder="Fecha de Registro" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mb-6">
                        <button type="button" id="crear-evaluacion" class="px-4 py-2 w-[20%] rounded bg-red-600 text-white hover:bg-gray-600 focus:outline-none transition-colors">
                            Crear Evaluación
                        </button>
                    </form>
                </div>
            </div>
            <hr class="border-2 m-4 mt-1">
        </section>
        <section class="m-4">
            <table class="w-full bg-white text-left text-sm text-gray-900 rounded">
                <thead class="bg-gray-50 text-center">
                    <tr>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-l-md">ID del Usuario</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Servicios</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Calificación</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Comentario</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Estatus</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Fecha de Registro</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-r-md"></th>
                    </tr>
                </thead>
                <tbody class="bg-gray-200">
                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">1</th>
                        <th class="text-center">Servicios de nutrición</th>
                        <th class="text-center">Buena</th>
                        <th class="text-center">Tienen buen servicio de nutrición</th>
                        <th class="text-center">Activo</th>
                        <th class="text-center">15-Agosto-2024 10:00</th>
                        <th class="flex justify-center">
                            <button type="button" id="editar-evaluacion" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar
                            </button>
                        </th>
                    </tr>
                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">2</th>
                        <th class="text-center">Horarios y precios </th>
                        <th class="text-center">Regular</th>
                        <th class="text-center">Deberian manejar mas horarios flexibles para los estudiantes</th>
                        <th class="text-center">Activo</th>
                        <th class="text-center">16-Agosto-2024 10:00</th>
                        <th class="flex justify-center">
                            <button type="button" id="editar-evaluacion" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar
                            </button>
                        </th>
                    </tr>
                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">3</th>
                        <th class="text-center">Programas de entretenimiento</th>
                        <th class="text-center">Buena</th>
                        <th class="text-center">Los programas que llegan a hacer y son buenos</th>
                        <th class="text-center">Activo</th>
                        <th class="text-center">15-Agosto-2024 10:00</th>
                        <th class="flex justify-center">
                            <button type="button" id="editar-evaluacion" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar
                            </button>
                        </th>
                    </tr>
                    
                    <!-- Aquí se pueden agregar más filas como en el ejemplo anterior -->
                </tbody>
            </table>
            <hr class="border-2 mt-4">
        </section>
    </main>
</template>

<script>
export default {
  name: 'EvaluacionesServicios',
  // Aquí puedes agregar lógica para manejar el formulario y los datos de la tabla
}
</script>

<style scoped>
/* Puedes agregar estilos específicos para esta vista si es necesario */
</style>
