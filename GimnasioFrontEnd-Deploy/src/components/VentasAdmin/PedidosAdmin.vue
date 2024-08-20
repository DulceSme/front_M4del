<template>
  <div>
    <h1 class="text-2xl xl:text-3xl font-extrabold mb-6">Gestión de Pedidos</h1>

    <!-- Formulario para añadir un nuevo pedido -->
    <form @submit.prevent="addOrder">
      <input
        v-model="newOrder.Producto"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Nombre de Producto" required
      />
      <input
        v-model="newOrder.Cantidad"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="number" placeholder="Cantidad" required
      />
      <input
        v-model="newOrder.FechaPedido"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="date" placeholder="Fecha del Pedido" required
      />
      <input
        v-model="newOrder.ProductoID"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Producto ID" required
      />
      <select
        v-model="newOrder.Tipo"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        required
      >
        <option value="" disabled>Selecciona un tipo</option>
        <option value="Promoción">Promoción</option>
        <option value="Descuento">Descuento</option>
        <option value="Precio Tienda">Precio Tienda</option>
      </select>
      <input
        v-model="newOrder.Estatus"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Estatus" required
      />
      <input
        v-model="newOrder.FechaActualizacion"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="date" placeholder="Fecha Actualización" required
      />
      <button
        class="mt-5 tracking-wide font-semibold bg-green-700 text-green-100 w-full py-4 rounded-lg hover:bg-green-900 transition-all duration-300 ease-in-out flex items-center justify-center focus:shadow-outline focus:outline-none col-span-2"
        type="submit"
      >
        Registrar Pedido
      </button>
    </form>

    <!-- Listado de pedidos -->
    <h2 class="text-xl font-bold mt-10">Lista de Pedidos</h2>
    <table class="min-w-full bg-white mt-5">
      <thead>
        <tr>
          <th class="py-2">ID</th>
          <th class="py-2">Nombre de Producto</th>
          <th class="py-2">Cantidad</th>
          <th class="py-2">Fecha del Pedido</th>
          <th class="py-2">Producto ID</th>
          <th class="py-2">Tipo</th>
          <th class="py-2">Estatus</th>
          <th class="py-2">Fecha Actualización</th>
          <th class="py-2">Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="order in orders" :key="order.id">
          <td class="border px-4 py-2">{{ order.id }}</td>
          <td class="border px-4 py-2">{{ order.Producto }}</td>
          <td class="border px-4 py-2">{{ order.Cantidad }}</td>
          <td class="border px-4 py-2">{{ order.FechaPedido }}</td>
          <td class="border px-4 py-2">{{ order.ProductoID }}</td>
          <td class="border px-4 py-2">{{ order.Tipo }}</td>
          <td class="border px-4 py-2">{{ order.Estatus }}</td>
          <td class="border px-4 py-2">{{ order.FechaActualizacion }}</td>
          <td class="border px-4 py-2 text-center">
            <div class="flex justify-center gap-2">
              <button @click="editOrder(order.id)" class="bg-yellow-500 text-white px-4 py-2 rounded-lg w-24">
                Editar
              </button>
              <button @click="deleteOrder(order.id)" class="bg-red-500 text-white px-4 py-2 rounded-lg w-24">
                Eliminar
              </button>
            </div>
          </td>
        </tr>
      </tbody>
    </table>

    <!-- Formulario para editar un pedido -->
    <div v-if="editingOrder">
      <h2 class="text-xl font-bold mt-10">Editar Pedido</h2>
      <form @submit.prevent="updateOrder">
        <input
          v-model="currentOrder.Producto"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Nombre de Producto" required
        />
        <input
          v-model="currentOrder.Cantidad"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="number" placeholder="Cantidad" required
        />
        <input
          v-model="currentOrder.FechaPedido"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="date" placeholder="Fecha del Pedido" required
        />
        <input
          v-model="currentOrder.ProductoID"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Producto ID" required
        />
        <select
          v-model="currentOrder.Tipo"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          required
        >
          <option value="" disabled>Selecciona un tipo</option>
          <option value="Promoción">Promoción</option>
          <option value="Descuento">Descuento</option>
          <option value="Precio Tienda">Precio Tienda</option>
        </select>
        <input
          v-model="currentOrder.Estatus"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Estatus" required
        />
        <input
          v-model="currentOrder.FechaActualizacion"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="date" placeholder="Fecha Actualización" required
        />
        <button
          class="mt-5 tracking-wide font-semibold bg-blue-700 text-gray-100 w-full py-4 rounded-lg hover:bg-blue-900 transition-all duration-300 ease-in-out flex items-center justify-center focus:shadow-outline focus:outline-none col-span-2"
          type="submit"
        >
          Actualizar Pedido
        </button>
        <br>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      orders: [
        { id: 1, Producto: "Producto A", Cantidad: 5, FechaPedido: "2024-08-01", ProductoID: "P123", Tipo: "Promoción", Estatus: "Pendiente", FechaActualizacion: "2024-08-01" },
        { id: 2, Producto: "Producto B", Cantidad: 10, FechaPedido: "2024-08-03", ProductoID: "P124", Tipo: "Descuento", Estatus: "En Proceso", FechaActualizacion: "2024-08-03" },
        { id: 3, Producto: "Producto C", Cantidad: 2, FechaPedido: "2024-08-05", ProductoID: "P125", Tipo: "Precio Tienda", Estatus: "Completado", FechaActualizacion: "2024-08-05" }
      ],
      newOrder: {
        Producto: "",
        Cantidad: "",
        FechaPedido: "",
        ProductoID: "",
        Tipo: "",
        Estatus: "",
        FechaActualizacion: ""
      },
      currentOrder: null,
      editingOrder: false
    };
  },
  methods: {
    addOrder() {
      if (this.newOrder.Producto && this.newOrder.Cantidad && this.newOrder.FechaPedido && this.newOrder.ProductoID && this.newOrder.Tipo && this.newOrder.Estatus && this.newOrder.FechaActualizacion) {
        const newId = this.orders.length ? Math.max(...this.orders.map(o => o.id)) + 1 : 1;
        this.orders.push({ ...this.newOrder, id: newId });
        this.newOrder = { Producto: "", Cantidad: "", FechaPedido: "", ProductoID: "", Tipo: "", Estatus: "", FechaActualizacion: "" };
      }
    },
    editOrder(id) {
      this.currentOrder = { ...this.orders.find(o => o.id === id) };
      this.editingOrder = true;
    },
    updateOrder() {
      const index = this.orders.findIndex(o => o.id === this.currentOrder.id);
      if (index !== -1) {
        this.orders.splice(index, 1, this.currentOrder);
      }
      this.currentOrder = null;
      this.editingOrder = false;
    },
    deleteOrder(id) {
      this.orders = this.orders.filter(o => o.id !== id);
    }
  }
};
</script>
