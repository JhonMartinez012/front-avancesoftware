<template>
  <div class="w-full my-6">
    <div class="w-full overflow-x-auto relative shadow-md sm:rounded-lg">
      <h2 class="w-full font-bold text-2xl text-blue-600">
        Listado de información
      </h2>
      <table
        class="w-full text-sm text-left text-gray-500 dark:text-gray-400 mt-5"
      >
        <thead
          class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400"
        >
          <tr>
            <th scope="col" class="py-3 px-6">Id</th>
            <th scope="col" class="py-3 px-6">Titulo</th>
            <th scope="col" class="py-3 px-6">Completada</th>
            <th scope="col" class="py-3 px-6">Id Usuario</th>
            <th scope="col" class="py-3 px-6">Accion</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="info in informacion"
            :key="info.id"
            class="bg-white border-b dark:bg-gray-900 dark:border-gray-700"
          >
            <td class="py-4 px-6">{{ info.id }}</td>
            <td class="py-4 px-6">{{ info.title }}</td>
            <td class="py-4 px-6">
              {{ info.completed === false ? 'No completada' : 'Completada' }}
            </td>
            <td class="py-4 px-6">{{ info.userId }}</td>

            <td class="py-4 px-6">
              <button
                class="font-medium text-blue-600 dark:text-blue-500 hover:underline"
                @click="editInfo(info.id)"
              >
                Edit
              </button>
              |
              <button
                class="font-medium text-blue-600 dark:text-blue-500 hover:underline"
                @click="deleteInfo(info.id)"
              >
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Principal',
  data() {
    return {
      informacion: [],
    }
  },

  mounted() {
    this.getInformacion()
  },

  methods: {
    getInformacion() {
      this.informacion = JSON.parse(localStorage.getItem('informacion'))
    },
    editInfo(id) {
      this.$router.push(`/${id}`)
    },
    deleteInfo(id) {
      const currentInfo = JSON.parse(localStorage.getItem('informacion'))
      const nuevaInfo = currentInfo.filter((info) => info.id !== id)
      localStorage.setItem('informacion', JSON.stringify(nuevaInfo))
      alert('Información eliminada')
      this.getInformacion()
    },
  },
}
</script>

<style></style>
