<template>
  <div>
    <div class="row">
      <div class="col-12 mb-4">
        <progress-bar :porcentaje="porcentaje" />
      </div>
      <div class="col-12 col-md-4">
        <form @submit.prevent="registrarProyecto">
          <div class="mb-3">
            <label class="form-label">Proyecto</label>
            <input
              v-model.trim="proyecto"
              required
              type="text"
              class="form-control"
            />
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
            <label for="exampleInputPassword1" class="form-check-label"
              >Urgente</label
            >
            <input v-model="urgente" type="checkbox" class="form-check-input" />
          </div>

          <button type="submit" class="btn btn-primary">Guardar</button>
        </form>
      </div>
      <div class="col-12 col-md-8">
        <total-proyectos
        :limpiar="limpiar"
          :numeroProyectos="numeroProyectos"
          :proyectos="proyectos"
          :cambiarEstado="cambiarEstado"
          :cambiarCompleto="cambiarCompleto"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ProgressBar from "./ProgressBar.vue";
import TotalProyectos from "./TotalProyectos.vue";
export default {
  components: {
    ProgressBar,
    TotalProyectos,
  },
  data: () => ({
    proyecto: "",
    tipo: "",
    urgente: false,
    proyectos: [],
    completado: false,
  }),
  methods: {
    limpiar(){
    console.log("ddd");
 this.proyectos = []
    localStorage.clear()
   },
    cambiarEstado(index) {
      this.proyectos[index].urgente = !this.proyectos[index].urgente;
      this.saveData()
    },
    cambiarCompleto(index) {
      this.proyectos[index].completado = !this.proyectos[index].completado;
      this.saveData()
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
      this.saveData()
      this.proyecto = "";
      this.tipo = "";
      this.urgente = false;
    },
    saveData(){
      localStorage.setItem("proyectos", JSON.stringify(this.proyectos))

    },
  },
  computed: {
    numeroProyectos() {
      return this.proyectos.length;
    },
    porcentaje() {
      let completados = 0;
      this.proyectos.map((proyecto) => {
        if (proyecto.completado) completados++;
      });
      console.log((completados * 100) / this.numeroProyectos);
      return (completados * 100) / this.numeroProyectos || 0;
    },
  },
  mounted() {
  this.proyectos =  JSON.parse(localStorage.getItem("proyectos")) || []
  },
};
</script>

<style></style>
