<template>
  <div class="container mt-3">
    <Header />
    <Formularios />
    <hr />
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Formularios from "./components/Formularios.vue";

  export default {
    components: {
      Header, Formularios
    },
  }
</script>