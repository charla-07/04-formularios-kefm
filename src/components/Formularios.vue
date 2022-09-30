<template>
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
  <hr>
  <div class="table-responsive">
    <table class="table table-dark table-hover">
      <thead>
        <tr>
          <th>#</th>
          <th>Proyecto</th>
          <th>Tipo</th>
          <th>Urgente</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>App con Laravel</td>
          <td>Laravel</td>
          <td class="bg-danger">Si/No</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
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
        };


        this.proyectos.push(proyecto)
        console.log(this.proyectos);

        this.proyecto = "";
        this.tipo = "";
        this.urgente = false;
      },
    },
  };

</script>