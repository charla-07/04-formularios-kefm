<template>
    <div class="row">
      <div class="col-12 col-md-3">
        <h1>Formularios</h1>
      </div>
      <div class="col-12 col-md-6">
        <img :src="url" alt="msg" width="100">
      </div>
    </div>
</template>

<script>
    export default {
      data: () => ({
        url: "https://cdn.svgporn.com/logos/vue.svg",
        msg: "Vue.js",
      })
    }
</script>