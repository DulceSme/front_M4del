<template>
    <h1 class="title-gym text-center">Promociones</h1>
    <section class="m-4">
            <table class="w-full bg-white text-left text-sm text-gray-900 rounded ">
                <thead class="bg-gray-50 text-center">
                    <tr>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-l-md">Nombre de Producto</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Marca</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Precio</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Tipo</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Fecha de creacion</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-r-md"></th>
                    </tr>
                </thead>
                <tbody class="bg-gray-200">
                    <tr class="hover:bg-gray-500 ">
                        <th class="h-[50px] text-center">
                            <span>Proteína Whey</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>FoodFort</span>
                        </th>
                        <th class="text-center">
                            <span>$589.20</span>
                        </th>
                        <th class="text-center">
                            <span>2X1</span>
                        </th>
                        <th class="text-center">
                            <span>03-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <a href="../Ventas/PedidoView.vue">
                                <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-gray-900 text-white hover:bg-gray-600">
                                    Agregar al carrito
                                </button>
                            </a>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>BCAA</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>Sport</span>
                        </th>
                        <th class="text-center">
                            <span>$520.00</span>
                        </th>
                        <th class="text-center">
                            <span>-15%</span>
                        </th>
                        <th class="text-center">
                            <span>05-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <a href="../Ventas/PedidoView.vue">
                                <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-gray-900 text-white hover:bg-gray-600">
                                    Agregar al carrito
                                </button>
                            </a>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>Multivitamínico</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>BodyCrunch</span>
                        </th>
                        <th class="text-center">
                            <span>$200.00</span>
                        </th>
                        <th class="text-center">
                            <span>-50%</span>
                        </th>
                        <th class="text-center">
                            <span>03-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <a href="../Ventas/PedidoView.vue">
                                <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-gray-900 text-white hover:bg-gray-600">
                                    Agregar al carrito
                                </button>
                            </a>
                        </th>
                    </tr>
             
                </tbody>
            </table>
            <hr class="border-2 mt-4">
        </section>
</template>