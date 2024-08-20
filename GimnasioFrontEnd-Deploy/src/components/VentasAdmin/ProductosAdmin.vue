<template>
    <div>
      <h1 class="title-gym">BULL'S GYM</h1>
      <main class="w-[100%] h-auto ml-2">
        <section>
          <div class="mx-auto p-4">
            <div class="bg-gray-900 dark:bg-gray-700 shadow rounded-lg p-6">
              <h1 class="text-xl font-semibold mb-4 text-gray-100 dark:text-gray-100">Agregar Productos</h1>
              <p class="text-gray-100 dark:text-gray-100 mb-6">
                Ingresa la información Correspondiente para crear un nuevo producto.
              </p>
              <form @submit.prevent="agregarProducto">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                  <input v-model="nuevoProducto.nombre" type="text" placeholder="Nombre de Producto"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                  <input v-model="nuevoProducto.marca" type="text" placeholder="Marca"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                  <input v-model="nuevoProducto.precio" type="text" placeholder="Precio Actual"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                  <input v-model="nuevoProducto.codigoBarras" type="text" placeholder="Codigo de barras"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                  <input v-model="nuevoProducto.descripcion" type="text" placeholder="Descripción"
                         class="border p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                  <select v-model="nuevoProducto.presentacion"
                          class="rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                    <option value="">Presentacion</option>
                    <option value="patillas">Pastillas</option>
                    <option value="malteadas">Malteadas</option>
                    <option value="polvos">Polvos</option>
                  </select>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                  <input v-model="nuevoProducto.estatus" type="text" placeholder="Estatus"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                  <input v-model="nuevoProducto.fechaRegistro" type="text" placeholder="Fecha registro"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                  <input v-model="nuevoProducto.fechaActualizacion" type="text" placeholder="Fecha actualizacion"
                         class="p-2 rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                  <select v-model="nuevoProducto.tipo"
                          class="rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                    <option value="">Tipo</option>
                    <option value="promocion">Promoción</option>
                    <option value="precioTienda">Precio Tienda</option>
                  </select>
                </div>
                <button type="submit" class="px-1 py-1 w-[30%] rounded bg-red-600 text-white hover:bg-gray-600 focus:outline-none transition-colors">
                  Agregar Producto
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
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-l-md">Nombre de Producto</th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Marca</th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Precio</th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Fecha de creacion</th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Fecha de Actualización</th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100">Promoción</th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100"></th>
              <th scope="col" class="px-6 py-4 bg-gray-900 font-medium text-gray-100 rounded-r-md"></th>
            </tr>
            </thead>
            <tbody class="bg-gray-200">
            <tr v-for="producto in productos" :key="producto.nombre" class="hover:bg-gray-500">
              <td class="h-[50px] text-center"><span>{{ producto.nombre }}</span></td>
              <td class="h-[50px] text-center"><span>{{ producto.marca }}</span></td>
              <td class="text-center"><span>{{ producto.precio }}</span></td>
              <td class="text-center"><span>{{ producto.fechaCreacion }}</span></td>
              <td class="text-center"><span>{{ producto.fechaActualizacion }}</span></td>
              <td class="text-center"><span>{{ producto.promocion ? 'SI' : 'NO' }}</span></td>
              <td class="text-center">
                <button @click="editarProducto(producto)" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-gray-600">
                  Editar Producto
                </button>
              </td>
              <td class="text-center">
                <button @click="eliminarProducto(producto)" class="px-4 mt-1 py-2 rounded-md bg-gray-900 text-white hover:bg-gray-600">
                  Eliminar
                </button>
              </td>
            </tr>
            </tbody>
          </table>
          <hr class="border-2 mt-4">
        </section>
      </main>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nuevoProducto: {
          nombre: '',
          marca: '',
          precio: '',
          codigoBarras: '',
          descripcion: '',
          presentacion: '',
          estatus: '',
          fechaRegistro: '',
          fechaActualizacion: '',
          tipo: ''
        },
        productos: [
          {
            nombre: 'Proteína Whey',
            marca: 'FoodFort',
            precio: '589.20',
            fechaCreacion: '03-Agosto-2024',
            fechaActualizacion: '08-Agosto-2024',
            promocion: true
          },
          {
            nombre: 'Creatina Monohidratada',
            marca: 'Flash',
            precio: '600.00',
            fechaCreacion: '04-Agosto-2024',
            fechaActualizacion: '08-Agosto-2024',
            promocion: false
          },
          {
            nombre: 'BCAA',
            marca: 'Sport',
            precio: '520.00',
            fechaCreacion: '05-Agosto-2024',
            fechaActualizacion: '08-Agosto-2024',
            promocion: true
          },
          {
            nombre: 'Pre-entrenador',
            marca: 'Train',
            precio: '400.00',
            fechaCreacion: '06-Agosto-2024',
            fechaActualizacion: '08-Agosto-2024',
            promocion: false
          },
          {
            nombre: 'Multivitamínico',
            marca: 'BodyCrunch',
            precio: '200.00',
            fechaCreacion: '03-Agosto-2024',
            fechaActualizacion: '08-Agosto-2024',
            promocion: true
          },
          {
            nombre: 'Proteína Vegana',
            marca: 'GreenProtein',
            precio: '620.00',
            fechaCreacion: '03-Agosto-2024',
            fechaActualizacion: '08-Agosto-2024',
            promocion: true
          }
        ]
      };
    },
    methods: {
  agregarProducto() {
    // Lógica para agregar el producto a la lista
    this.productos.push({ ...this.nuevoProducto });
    // Limpiar el formulario
    this.nuevoProducto = {
      nombre: '',
      marca: '',
      precio: '',
      codigoBarras: '',
      descripcion: '',
      presentacion: '',
      estatus: '',
      fechaRegistro: '',
      fechaActualizacion: '',
      tipo: ''
    };
  },
  editarProducto(producto) {
    // Lógica para editar un producto
    this.nuevoProducto = { ...producto };
  },
  eliminarProducto(producto) {
    this.productos = this.productos.filter(e => e !== producto);
  }
}

  };
  </script>
  
  <style scoped>
  /* Estilos personalizados */
  </style>
  