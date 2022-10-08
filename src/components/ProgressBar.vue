<template>
    <h3 class="text-center">Progreso: {{porcentaje}}%</h3>
    <div class="progress">
        <div class="progress-bar progress-bar-striped progress-bar-animated bg-success" role="progressbar"
        :style="`width: ${porcentaje}%`" :aria-valuenow="porcentaje" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
</template>

<script>
    export default {
        props: {
            porcentaje: Number,
            
        }
    }
</script>