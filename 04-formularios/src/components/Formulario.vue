<template>
  <div>



    <div class="row">
      <div class="col-12 mb-4">
        <h3 class="text-center">
          Progreso:0%
        </h3>
        <div class="progress">
          <div class="progress-bar progress-bar-striped progress-bar-animated bg-success" role="progressbar"
            aria-valuenow="25" aria-valuemin="0" aria-valuemax="100" style="width: 25%;"></div>
        </div>
      </div>
      <div class="col-12 col-md-4">
        <form @submit.prevent="registrarProyecto">
          <div class="mb-3">
            <label class="form-label">Proyecto</label>
            <input v-model.trim="proyecto" required type="text" class="form-control" />
          </div>
          <div class="mb-3">
            <label class="form-label">Actividad</label>
            <select v-model="tipo" class="form-select" required>
              <option disabled selected value="">Seleccione un tipo...</option>
              <option>Aplicacion web con vue</option>
              <option>Backend service con node.js</option>
              <option>App movil con react native</option>
            </select>
          </div>

          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-check-label">Urgente</label>
            <input v-model="urgente" type="checkbox" class="form-check-input" />
          </div>

          <button type="submit" class="btn btn-primary">Guardar</button>
        </form>
      </div>
      <div class="col-12 col-md-8">
        <h3>Total Proyectos: {{ numeroProyectos }}</h3>
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
                <td @click="cambiarEstado(index)" :class="pryecto.urgente ? 'bg-success' : 'bg-danger'">{{ pryecto.urgente
                  ? "SI":"NO"}}</td>
                <td @click="cambiarCompleto(index)" :class="pryecto.completado ? 'bg-success' : 'bg-danger'">{{
                  pryecto.completado ? "Completo" : "Incompleto"}}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    proyecto: "",
    tipo: "",
    urgente: false,
    proyectos: [],
    completado: false,
  }),
  methods: {
    cambiarEstado(index) {
      this.proyectos[index].urgente = !this.proyectos[index].urgente
    },
    cambiarCompleto(index) {
      this.proyectos[index].completado = !this.proyectos[index].completado
    },
    registrarProyecto() {
      const proyecto = {
        proyecto: this.proyecto,
        tipo: this.tipo,
        urgente: this.urgente,
        completado: false,
      };
      console.log(proyecto);

      this.proyectos.push(proyecto);
      this.proyecto = "";
      this.tipo = "";
      this.urgente = false;
    },
  },
  computed: {
    numeroProyectos() {
      return this.proyectos.length
    }
  },
};
</script>

<style></style>
