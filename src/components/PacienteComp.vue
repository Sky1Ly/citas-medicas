<template>
    <div>
        <div :class="cardClass" class="card mt-3" style="max-width: 18rem;">
            <div class="card-header bg-transparent d-flex justify-content-center">
                <h3>{{ paciente }}</h3>
            </div>
            <div class="card-body">
                <p class="card-text">Motivo consulta: {{ motivoConsulta }}</p>
                <p class="card-text">Fecha: {{ fecha }}</p>
                <p class="card-text">Hora: {{ hora }}</p>
            </div>
            <div class="card-footer bg-transparent d-flex justify-content-center">
                <button 
                    type="button" 
                    :class="buttonClass" 
                    class="btn"
                    @click="$emit('eliminarPaciente')">Eliminar</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["id", "paciente", "fecha", "hora", "motivoConsulta", "gravedad"],
    computed: {
        cardClass() {
            switch (this.gravedad) {
                case 'Baja':
                    return 'text-bg-success'
                    break;

                case 'Media':
                    return 'text-bg-warning'
                    break;

                case 'Alta':
                    return 'text-bg-danger'
                    break;

                default:
                    return 'btn-outline-dark'
                    break;
            }
        },

        buttonClass() {
            if (this.gravedad === 'Baja' || this.gravedad === 'Alta') {
                return 'btn-outline-light'
            } else {
                return 'btn-outline-dark'
            }
        }
    }
}
</script>

<style></style>