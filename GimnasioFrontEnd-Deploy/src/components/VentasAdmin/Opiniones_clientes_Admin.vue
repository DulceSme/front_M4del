<template>
  <div>
    <h1 class="text-2xl xl:text-3xl font-extrabold mb-6">Opiniones Clientes</h1>

    <!-- Formulario para añadir un nuevo programa -->
    <form @submit.prevent="addProgram">
      <input
        v-model="newProgram.Descripcion"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Descripcion" required
      />
      <input
        v-model="newProgram.Tipo"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Tipo" required
      />
      <input
        v-model="newProgram.Respuesta"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Respuesta" required
      />
      <input
        v-model="newProgram.Estatus"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Estatus" required
      />
      <input
        v-model="newProgram.Registro"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="date" placeholder="Fecha Registro" required
      />
      <input
        v-model="newProgram.Actualizacion"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="date" placeholder="Fecha Actualizacion" required
      />
      <input
        v-model="newProgram.Atencion"
        class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
        type="text" placeholder="Atencion Personal" required
      />
      <button
        class="mt-5 tracking-wide font-semibold bg-red-700 text-red-100 w-full py-4 rounded-lg hover:bg-red-900 transition-all duration-300 ease-in-out flex items-center justify-center focus:shadow-outline focus:outline-none col-span-2"
        type="submit"
      >
        Registrar
      </button>
    </form>

    <!-- Listado de programas -->
    <h2 class="text-xl font-bold mt-10">Lista de Opiniones Clientes</h2>
    <table class="min-w-full bg-white mt-5">
      <thead>
        <tr>
          <th class="py-2">ID</th>
          <th class="py-2">Descripcion</th>
          <th class="py-2">Tipo</th>
          <th class="py-2">Respuesta</th>
          <th class="py-2">Estatus</th>
          <th class="py-2">Atencion Personal</th>
          <th class="py-2">Fecha Registro</th>
          <th class="py-2">Fecha Actualizacion</th>
          <th class="py-2">Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="program in programs" :key="program.id">
          <td class="border px-4 py-2">{{ program.id }}</td>
          <td class="border px-4 py-2">{{ program.Descripcion }}</td>
          <td class="border px-4 py-2">{{ program.Tipo }}</td>
          <td class="border px-4 py-2">{{ program.Respuesta }}</td>
          <td class="border px-4 py-2">{{ program.Estatus }}</td>
          <td class="border px-4 py-2">{{ program.Atencion }}</td>
          <td class="border px-4 py-2">{{ program.Registro }}</td>
          <td class="border px-4 py-2">{{ program.Actualizacion }}</td>
          <td class="border px-4 py-2">
            <button @click="editProgram(program.id)" class="bg-yellow-500 text-white px-4 py-2 rounded">
              Editar
            </button>
            <button @click="deleteProgram(program.id)" class="bg-red-500 text-white px-4 py-2 rounded ml-2">
              Eliminar
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <!-- Formulario para editar un programa -->
    <div v-if="editingProgram">
      <h2 class="text-xl font-bold mt-10">Editar Opinion</h2>
      <form @submit.prevent="updateProgram">
        <input
          v-model="currentProgram.Descripcion"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Descripcion" required
        />
        <input
          v-model="currentProgram.Tipo"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Tipo" required
        />
        <input
          v-model="currentProgram.Respuesta"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Respuesta" required
        />
        <input
          v-model="currentProgram.Estatus"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Estatus" required
        />
        <input
          v-model="currentProgram.Atencion"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="text" placeholder="Atencion Personal" required
        />
        <input
          v-model="currentProgram.Registro"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="date" placeholder="Fecha Registro" required
        />
        <input
          v-model="currentProgram.Actualizacion"
          class="w-full px-8 py-4 rounded-lg font-medium bg-gray-100 border border-gray-200 placeholder-gray-500 text-sm focus:outline-none focus:border-gray-400 focus:bg-white mt-5"
          type="date" placeholder="Fecha Actualizacion" required
        />
        <button
          class="mt-5 tracking-wide font-semibold bg-blue-700 text-gray-100 w-full py-4 rounded-lg hover:bg-blue-900 transition-all duration-300 ease-in-out flex items-center justify-center focus:shadow-outline focus:outline-none col-span-2"
          type="submit"
        >
          Actualizar
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
      programs: [
        { id: 1, Descripcion: "Programa de Nutrición", Tipo: "Activo", Respuesta: "Buena", Estatus: "Activo", Atencion: "Excelente", Registro: "2024-01-15", Actualizacion: "2024-08-01" },
        { id: 2, Descripcion: "Entrenamiento Funcional", Tipo: "Inactivo", Respuesta: "Moderada", Estatus: "Inactivo", Atencion: "Adecuada", Registro: "2024-03-10", Actualizacion: "2024-07-25" },
        { id: 3, Descripcion: "Yoga Avanzado", Tipo: "Activo", Respuesta: "Excelente", Estatus: "Activo", Atencion: "Muy Buena", Registro: "2024-02-05", Actualizacion: "2024-08-10" }
      ],
      newProgram: {
        Descripcion: "",
        Tipo: "",
        Respuesta: "",
        Estatus: "",
        Registro: "",
        Actualizacion: "",
        Atencion: ""
      },
      currentProgram: null,
      editingProgram: false
    };
  },
  methods: {
    addProgram() {
      if (this.newProgram.Descripcion && this.newProgram.Tipo && this.newProgram.Respuesta && this.newProgram.Estatus && this.newProgram.Registro && this.newProgram.Actualizacion && this.newProgram.Atencion) {
        const newId = this.programs.length ? this.programs[this.programs.length - 1].id + 1 : 1;
        this.programs.push({ ...this.newProgram, id: newId });
        this.newProgram = { Descripcion: "", Tipo: "", Respuesta: "", Estatus: "", Registro: "", Actualizacion: "", Atencion: "" };
      }
    },
    editProgram(id) {
      this.currentProgram = { ...this.programs.find(p => p.id === id) };
      this.editingProgram = true;
    },
    updateProgram() {
      const index = this.programs.findIndex(p => p.id === this.currentProgram.id);
      if (index !== -1) {
        this.programs.splice(index, 1, this.currentProgram);
      }
      this.currentProgram = null;
      this.editingProgram = false;
    },
    deleteProgram(id) {
      this.programs = this.programs.filter(p => p.id !== id);
    }
  }
};
</script>
