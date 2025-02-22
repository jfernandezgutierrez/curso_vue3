<template>
   <div class="container mt-3">
      <Header/>
    <form @submit.prevent="addUser" v-if="f">
      <div>
        <label for="nombre">Nombre: </label>
        <input
          v-model="nombre"
          id="nombre"
          type="text"
          placeholder="Nombre"
          required
        />
      </div>
      <div>
        <label for="edad">Edad: </label>
        <input
          v-model="edad"
          id="edad"
          type="number"
          min="15"
          max="100"
          placeholder="Edad"
          required
        />
      </div>
      <div>
        <label for="email">Email: </label>
        <input
          v-model="correo"
          id="email"
          type="email"
          placeholder="email@mail.com"
          required
        />
      </div>
      <button type="submit">Enviar</button>
    </form>
    <!-- formulario de forms-->
   <Formulario/>
  </div>

</template>

<script>
import Formulario from './components/Formulario.vue';
import Header from './components/Header.vue';

export default {
   components:{
      Header,
      Formulario,
   },
  data: () => ({
   f:false,
    nombre: "",
    edad: 0,
    correo: "",
  }),
  methods: {
    addUser() {
      console.log();
    },
  },
};
</script>

<style>

</style>
