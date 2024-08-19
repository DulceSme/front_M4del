<template>
    <h1 class="title-gym text-center">Estatus de pedidos</h1>
        <section class="m-4">
            <table class="w-full bg-white text-left text-sm text-gray-900 rounded ">
                <thead class="bg-gray-50 text-center">
                    <tr>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-l-md">Nombre de Producto</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Cantidad</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Precio</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Fecha del pedido</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Estatus</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Aplica en</th>
                        <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-r-md"></th>
                    </tr>
                </thead>
                <tbody class="bg-gray-200">
                    <tr class="hover:bg-gray-500 ">
                        <th class="h-[50px] text-center">
                            <span>Proteína Whey</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>3</span>
                        </th>
                        <th class="text-center">
                            <span>$1760.60</span>
                        </th>
                        <th class="text-center">
                            <span>03-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <span>Proceso</span>
                        </th>
                        <th class="text-center">
                            <span>Pomoción</span>
                        </th>
                        <th class="flex justify-center">
                            <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar Pedido
                            </button>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>Creatina Monohidratada</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>4</span>
                        </th>
                        <th class="text-center">
                            <span>$2400.00</span>
                        </th>
                        <th class="text-center">
                            <span>04-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <span>Iniciado</span>
                        </th>
                        <th class="text-center">
                            <span>Precio tienda</span>
                        </th>
                        <th class="flex justify-center">
                            <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar Pedido
                            </button>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>BCAA</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>2</span>
                        </th>
                        <th class="text-center">
                            <span>$1040.00</span>
                        </th>
                        <th class="text-center">
                            <span>05-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <span>Entregado</span>
                        </th>
                        <th class="text-center">
                            <span>Promoción</span>
                        </th>
                        <th class="text-center">
                            <span>24-Noviembre-2024</span>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>Pre-entrenador</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>7</span>
                        </th>
                        <th class="text-center">
                            <span>$2800.00</span>
                        </th>
                        <th class="text-center">
                            <span>06-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <span>Iniciado</span>
                        </th>
                        <th class="text-center">
                            <span>Precio tienda</span>
                        </th>
                        <th class="flex justify-center">
                            <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar Pedido
                            </button>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>Multivitamínico</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>12</span>
                        </th>
                        <th class="text-center">
                            <span>$2400.00</span>
                        </th>
                        <th class="text-center">
                            <span>03-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <span>Proceso</span>
                        </th>
                        <th class="text-center">
                            <span>Promoción</span>
                        </th>
                        <th class="flex justify-center">
                            <button type="button" id="producto" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                                Editar Pedido
                            </button>
                        </th>
                    </tr>

                    <tr class="hover:bg-gray-500">
                        <th class="h-[50px] text-center">
                            <span>Proteína Vegana</span>
                        </th>
                        <th class="h-[50px] text-center">
                            <span>9</span>
                        </th>
                        <th class="text-center">
                            <span>$4500.00</span>
                        </th>
                        <th class="text-center">
                            <span>04-Agosto-2024</span>
                        </th>
                        <th class="text-center">
                            <span>Entregado</span>
                        </th>
                        <th class="text-center">
                            <span>Precio tienda</span>
                        </th>
                        <th class="text-center">
                            <span>10-Agosto-2024</span>
                        </th>
                    </tr>
                </tbody>
            </table>
            <hr class="border-2 mt-4">
        </section>
</template>
