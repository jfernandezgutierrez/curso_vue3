<template>
  <div class="col-12 col-md-8">
    
    <h3>Total Proyectos: {{ numeroProyectos }}</h3>
<button class="btn btn-danger" @click="limpiar">Limpiar</button>
    <div class="table-responsive">
      <table class="table">
        <thead>
          <th>#</th>
          <th>Proyecto</th>
          <th>Tipo</th>
          <th>Urgente</th>
          <th>Completado</th>
        </thead>
        <tbody>
          <tr v-for="(pryecto, index) in proyectos" :key="index">
            <td>{{ index + 1 }}</td>
            <td>{{ pryecto.proyecto }}</td>
            <td>{{ pryecto.tipo }}</td>
            <td
              @click="cambiarEstado(index)"
              :class="pryecto.urgente ? 'bg-success' : 'bg-danger'"
            >
              {{ pryecto.urgente ? "SI" : "NO" }}
            </td>
            <td
              @click="cambiarCompleto(index)"
              :class="pryecto.completado ? 'bg-success' : 'bg-danger'"
            >
              {{ pryecto.completado ? "Completo" : "Incompleto" }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    numeroProyectos: Number,
    proyectos: Object,
    cambiarEstado: Function,
    cambiarCompleto: Function,
    limpiar:Function
  },
  methods:{
  
  }
};
</script>

<style>
</style>