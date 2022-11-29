<template>
  <form>
    <h1 class="font-semibold text-center text-blue-700 text-2xl my-5">
      Actualizando la info del id: {{ id }}
    </h1>
    <div class="grid gap-6 mb-6 md:grid-cols-2">
      <div>
        <label
          for="first_name"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Titulo</label
        >
        <input
          id="title"
          v-model="data.title"
          type="text"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="John"
          required
        />
      </div>
      <div>
        <label
          for="last_name"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Completada</label
        >
        <input
          id="completed"
          v-model="data.completed"
          type="text"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Doe"
          required
        />
      </div>
      <div>
        <label
          for="company"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Id usuario</label
        >
        <input
          id="userId"
          v-model="data.userId"
          type="text"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Flowbite"
          required
        />
      </div>
    </div>

    <button
      type="submit"
      class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      @click.prevent="updateInfo"
    >
      Actualizar
    </button>
  </form>
</template>

<script>
export default {
  name: 'EditInfo',
  data() {
    return {
      data: {},
    }
  },

  computed: {
    id() {
      return this.$route.params.id
    },
  },

  mounted() {
    this.getInformacionById()
  },

  methods: {
    getInformacionById() {
      const currentInfo = JSON.parse(localStorage.getItem('informacion'))
      const info = currentInfo.filter((info) => info.id === parseInt(this.id))
      this.data = info[0]
    },
    updateInfo() {
      const currentInfo = JSON.parse(localStorage.getItem('informacion'))
      const info = currentInfo.filter((info) => info.id === parseInt(this.id))
      info[0].title = this.data.title
      info[0].completed = this.data.completed
      info[0].userId = this.data.userId

      console.log(currentInfo)

      localStorage.setItem('informacion', JSON.stringify(currentInfo))
    },

  },
}
</script>

<style></style>
