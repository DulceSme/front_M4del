<template>
    <div>
      <h1 class="title-gym text-center">Estatus de pedidos</h1>
      <section class="m-4">
        <button @click="openAddOrderForm" class="px-4 py-2 rounded-md bg-red-600 text-white hover:bg-red-700 transition-colors mb-4">
          Agregar Pedido
        </button>
        <table class="w-full bg-white text-left text-sm text-gray-900 rounded">
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
            <tr v-for="(order, index) in orders" :key="index" class="hover:bg-gray-500">
              <td class="h-[50px] text-center">{{ order.productName }}</td>
              <td class="h-[50px] text-center">{{ order.quantity }}</td>
              <td class="text-center">{{ order.price }}</td>
              <td class="text-center">{{ order.orderDate }}</td>
              <td class="text-center">{{ order.status }}</td>
              <td class="text-center">{{ order.appliesTo }}</td>
              <td class="flex justify-center">
                <button @click="editOrder(order, index)" class="px-4 mt-1 py-2 rounded-md bg-red-600 text-white hover:bg-red-700 transition-colors">
                  Editar Pedido
                </button>
              </td>
            </tr>
          </tbody>
        </table>
        <hr class="border-2 mt-4">
      </section>
  
      <!-- Formulario para agregar pedido -->
      <div v-if="showAddOrderForm" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-50 z-50">
        <div class="bg-white p-6 rounded-lg shadow-lg w-[90%] md:w-[50%]">
          <h2 class="text-lg font-semibold mb-4">Agregar Pedido</h2>
          <form @submit.prevent="addOrder">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
              <input v-model="newOrder.productName" type="text" placeholder="Nombre de Producto" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <input v-model="newOrder.quantity" type="number" placeholder="Cantidad" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <input v-model="newOrder.price" type="text" placeholder="Precio" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <input v-model="newOrder.orderDate" type="date" placeholder="Fecha del pedido" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <select v-model="newOrder.status" class="rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                <option value="">Estatus</option>
                <option value="Proceso">Proceso</option>
                <option value="Iniciado">Iniciado</option>
                <option value="Entregado">Entregado</option>
              </select>
              <select v-model="newOrder.appliesTo" class="rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                <option value="">Aplica en</option>
                <option value="Promoción">Promoción</option>
                <option value="Precio tienda">Precio tienda</option>
              </select>
            </div>
            <div class="flex justify-end gap-4">
              <button type="button" @click="closeAddOrderForm" class="px-4 py-2 rounded-md bg-gray-500 text-white hover:bg-gray-600 transition-colors">
                Cancelar
              </button>
              <button type="submit" class="px-4 py-2 rounded-md bg-red-600 text-white hover:bg-red-700 transition-colors">
                Agregar Pedido
              </button>
            </div>
          </form>
        </div>
      </div>
  
      <!-- Formulario para editar pedido -->
      <div v-if="showEditOrderForm" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-50 z-50">
        <div class="bg-white p-6 rounded-lg shadow-lg w-[90%] md:w-[50%]">
          <h2 class="text-lg font-semibold mb-4">Editar Pedido</h2>
          <form @submit.prevent="updateOrder">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
              <input v-model="selectedOrder.productName" type="text" placeholder="Nombre de Producto" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <input v-model="selectedOrder.quantity" type="number" placeholder="Cantidad" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <input v-model="selectedOrder.price" type="text" placeholder="Precio" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <input v-model="selectedOrder.orderDate" type="date" placeholder="Fecha del pedido" class="p-2 rounded-lg w-full font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
              <select v-model="selectedOrder.status" class="rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                <option value="">Estatus</option>
                <option value="Proceso">Proceso</option>
                <option value="Iniciado">Iniciado</option>
                <option value="Entregado">Entregado</option>
              </select>
              <select v-model="selectedOrder.appliesTo" class="rounded-lg w-full font-medium bg-gray-100 border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white">
                <option value="">Aplica en</option>
                <option value="Promoción">Promoción</option>
                <option value="Precio tienda">Precio tienda</option>
              </select>
            </div>
            <div class="flex justify-end gap-4">
              <button type="button" @click="closeEditOrderForm" class="px-4 py-2 rounded-md bg-gray-500 text-white hover:bg-gray-600 transition-colors">
                Cancelar
              </button>
              <button type="submit" class="px-4 py-2 rounded-md bg-red-600 text-white hover:bg-red-700 transition-colors">
                Actualizar Pedido
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        orders: [
          {
            productName: 'Proteína Whey',
            quantity: 3,
            price: '$1760.60',
            orderDate: '03-Agosto-2024',
            status: 'Proceso',
            appliesTo: 'Promoción'
          },
          // Agrega más pedidos aquí según sea necesario
        ],
        showAddOrderForm: false,
        showEditOrderForm: false,
        newOrder: {
          productName: '',
          quantity: '',
          price: '',
          orderDate: '',
          status: '',
          appliesTo: ''
        },
        selectedOrderIndex: null,
        selectedOrder: {
          productName: '',
          quantity: '',
          price: '',
          orderDate: '',
          status: '',
          appliesTo: ''
        }
      };
    },
    methods: {
      openAddOrderForm() {
        this.showAddOrderForm = true;
      },
      closeAddOrderForm() {
        this.showAddOrderForm = false;
      },
      addOrder() {
        if (this.newOrder.productName && this.newOrder.quantity && this.newOrder.price && this.newOrder.orderDate && this.newOrder.status && this.newOrder.appliesTo) {
          this.orders.push({ ...this.newOrder });
          this.newOrder = { productName: '', quantity: '', price: '', orderDate: '', status: '', appliesTo: '' };
          this.closeAddOrderForm();
        } else {
          alert('Por favor, completa todos los campos.');
        }
      },
      editOrder(order, index) {
        this.selectedOrder = { ...order };
        this.selectedOrderIndex = index;
        this.showEditOrderForm = true;
      },
      closeEditOrderForm() {
        this.showEditOrderForm = false;
      },
      updateOrder() {
        if (this.selectedOrderIndex !== null) {
          // Actualizar el pedido en el array
          this.$set(this.orders, this.selectedOrderIndex, { ...this.selectedOrder });
          this.selectedOrder = { productName: '', quantity: '', price: '', orderDate: '', status: '', appliesTo: '' };
          this.selectedOrderIndex = null;
          this.closeEditOrderForm();
          alert('Pedido actualizado con éxito.'); // Confirmación de éxito
        } else {
          alert('Pedido no encontrado.');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  /* Agrega estilos personalizados aquí si es necesario */
  </style>
  