<template>
  <div class="w-full">
    <div class="w-full h-screen flex flex-col items-center justify-center">
      <h1 class="font-bold text-3xl">PRUEBA FRONT AVANCESOFTWARE</h1>
      <nuxt-link
        to="/principal"
        class="text-lg font-semibold text-blue-700 hover:text-blue-600"
        >Pagina principal</nuxt-link
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'Index',
data() {
    return {
    }
  },
    
  mounted(){
    this.saveLocalStorage();
  },

  methods:{
    async saveLocalStorage(){
       const response=  await this.$axios.get('todos/');
        localStorage.setItem('informacion', JSON.stringify(response.data));
    }
  }
}
</script>

<style></style>
