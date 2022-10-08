<template>
  <hr>
  <div class="row">
    <div class="col-12 mb-4">
      <progress-bar :porcentaje="porcentaje"/>
    </div>
    <div class="col-12 col-md-4">
      <form @submit.prevent="registrarProyecto">
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Proyecto</label>
        <input v-model.trim="proyecto"  type="text" class="form-control" required >
      </div>
      <div class="mb-3">
        <label class="form-label">Actividad</label>
        <select v-model.trim="tipo" class="form-select">
          <option disabled selected value="">Selecciona una actividad</option>
          <option>Aplicaciones web con Vue.js</option>
          <option>BackEnd Services</option>
          <option>App móvil con Vue.js</option>
        </select>
      </div>
      <div class="form-check">
        <input v-model.trim="urgente" class="form-check-input" type="checkbox">
        <label class="form-check-label" for="flexRadioDefault1">
          Urgente
        </label>
      </div>

      <button type="submit" class="btn btn-primary">Guardar</button>
      </form>
    </div>
    <div class="col-12 col-md-8">
      <total-proyectos :numeroProyectos="numeroProyectos" :proyectos="proyectos" :cambiarEstado="cambiarEstado"/>
    </div>
  </div>
</template>

<script>
  import ProgressBar from './ProgressBar.vue';
  import TotalProyectos from './TotalProyectos.vue';
  export default {
    data: () => ({
      proyecto: "",
      tipo: "",
      urgente: false,
      proyectos: [],
    }),
    methods: {
      registrarProyecto(){
        const proyecto = {
          proyecto: this.proyecto,
          tipo: this.tipo,
          urgente: this.urgente,
          completado: false,
        };


        this.proyectos.push(proyecto);
        localStorage.setItem("proyectos", JSON.stringify(this.proyectos));
        console.log(this.proyectos);

        this.proyecto = "";
        this.tipo = "";
        this.urgente = false;
      },
      cambiarEstado(proyecto, campo){
        //this.proyectos[id].urgente = !this.proyectos[id].urgente;
        //console.log(proyecto, campo)
        proyecto[campo] = !proyecto[campo];
      }
    },

    computed: {
      numeroProyectos(){
        return this.proyectos.length;
      },
      porcentaje(){
        let completados = 0;

        this.proyectos.map(proyecto => {
          if(proyecto.completado) completados++;
        });

        return (completados * 100)/this.numeroProyectos || 0;
       
      },
    },

    components: {
      ProgressBar,
      TotalProyectos
    },

    mounted(){
      this.proyectos = JSON.parse(localStorage.getItem("proyectos")) || [];
    }
  };

</script>