<script>
  export default {
    data() {
      return {
        gravedades: ["Baja", "Media", "Alta"],
        pacienteTx: "",
        fecha: "",
        hora: "",        
        gravedad: "",
        motivoTx: "",
        conContenido: false,
        sinContenido: true
      }
    },
    methods: {
      textoRojo(){
        if (this.pacienteTx != '') {
          this.conContenido = true
          this.sinContenido = false
        }
        if (this.fecha != '') {
          this.conContenido = true
          this.sinContenido = false
        }
        if (this.hora != '') {
          this.conContenido = true
          this.sinContenido = false
        }
        if (this.motivoTx != '') {
          this.conContenido = true
          this.sinContenido = false
        }
      }
    },
  }
</script>

<template>
  <div class="container">
    <div class="row mt-5">
      <div class="col-sm-2 mb-3 text-center">
        <label for="paciente" class="form-label text-center" :class="{conContenido: conContenido, sinContenido: sinContenido}">Paciente</label>
        <input type="text" class="form-control" id="paciente" v-model="pacienteTx" @change="textoRojo"/>
      </div>
      <div class="col-sm-2 mb-3 text-center">
        <label for="fecha" class="form-label text-center" :class="{conContenido: conContenido, sinContenido: !conContenido}">Fecha</label>
        <input type="date" class="form-control" id="fecha" v-model="fecha" @change="textoRojo"/>
      </div>
      <div class="col-sm-2 mb-3 text-center">
        <label for="hora" class="form-label text-center" :class="{conContenido: conContenido, sinContenido: !conContenido}">Hora</label>
        <input type="time" class="form-control" id="hora" v-model="hora" @change="textoRojo"/>
      </div>
      <div class="col-sm-3 mb-3 text-center">
        <label class="form-label text-center" :class="{conContenido: conContenido, sinContenido: !conContenido}">Gravedad</label>
        <select class="form-select" aria-label="Default select example" v-model="gravedad">
          <option selected>Seleccione gravedad del paciente</option>
          <option v-for="(gravedad, i) in gravedades" :value=gravedad :key="i">{{gravedad}}</option>
        </select>
      </div>
      <div class="col-sm-3 mb-3 text-center">
        <label for="motivo" class="form-label text-center" :class="{conContenido: conContenido, sinContenido: !conContenido}">Motivo</label>
        <textarea class="form-control" id="motivo" rows="1" v-model="motivoTx" @change="textoRojo"></textarea>
      </div>
    </div>
    <div class="row">
      <div class="d-flex justify-content-center mt-3">
        <button type="button" class="btn btn-success w-25">Agregar Paciente</button>
      </div>
    </div>

    <p>{{ pacienteTx }}</p>
    <p>{{ fecha }}</p>
    <p>{{ hora }}</p>
    <p>{{ gravedad }}</p>
    <p>{{ motivoTx }}</p>
  </div>
</template>

<style>
  .conContenido {
    color: #000;
  }

  .sinContenido {
    color: red;
  }
</style>
