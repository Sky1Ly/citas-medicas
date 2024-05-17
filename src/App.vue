<script>
export default {
  data() {
    return {
      gravedades: ["Baja", "Media", "Alta"],
      pacientes: [],
      datos: {
        pacienteTx: "",
        fecha: "",
        hora: "",
        gravedad: "",
        motivoTx: ""
      },
      conContenido: {
        pacienteTx: false,
        fecha: false,
        hora: false,
        gravedad: false,
        motivoTx: false
      }
    }
  },
  methods: {
    textoRojo(index) {
      if (this.datos[index] != '') {
        this.conContenido[index] = true
      } else {
        this.conContenido[index] = false
      }
    }
  },
}
</script>

<template>
  <div class="container">
    <div class="row mt-5">
      <div class="col-sm-2 mb-3 text-center">
        <label for="paciente" class="form-label text-center"
          :class="{ sinContenido: !conContenido.pacienteTx }">Paciente</label>
        <input type="text" class="form-control" id="paciente" v-model="datos.pacienteTx" @input="textoRojo('pacienteTx')" />
      </div>
      <div class="col-sm-2 mb-3 text-center">
        <label for="fecha" class="form-label text-center"
          :class="{ sinContenido: !conContenido.fecha }">Fecha</label>
        <input type="date" class="form-control" id="fecha" v-model="datos.fecha" @input="textoRojo('fecha')" />
      </div>
      <div class="col-sm-2 mb-3 text-center">
        <label for="hora" class="form-label text-center"
          :class="{ sinContenido: !conContenido.hora }">Hora</label>
        <input type="time" class="form-control" id="hora" v-model="datos.hora" @input="textoRojo('hora')" />
      </div>
      <div class="col-sm-3 mb-3 text-center">
        <label class="form-label text-center"
          :class="{ sinContenido: !conContenido.gravedad }">Gravedad</label>
        <select class="form-select" aria-label="Default select example" v-model="datos.gravedad" @change="textoRojo('gravedad')">
          <option selected>Seleccione gravedad del paciente</option>
          <option v-for="(gravedad, i) in gravedades" :value=gravedad :key="i">{{ gravedad }}</option>
        </select>
      </div>
      <div class="col-sm-3 mb-3 text-center">
        <label for="motivo" class="form-label text-center"
          :class="{ sinContenido: !conContenido.motivoTx }">Motivo</label>
        <textarea class="form-control" id="motivo" rows="1" v-model="datos.motivoTx" @input="textoRojo('motivoTx')"></textarea>
      </div>
    </div>
    <div class="row">
      <div class="d-flex justify-content-center mt-3">
        <button type="button" class="btn btn-success w-25">Agregar Paciente</button>
      </div>
    </div>

    <p>{{ datos.pacienteTx }}</p>
    <p>{{ datos.fecha }}</p>
    <p>{{ datos.hora }}</p>
    <p>{{ datos.gravedad }}</p>
    <p>{{ datos.motivoTx }}</p>
  </div>
</template>

<style>
.sinContenido {
  color: red;
}
</style>
