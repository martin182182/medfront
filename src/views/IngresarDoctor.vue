<template>
    <div>
        <br><br><br>
       <b-card img-src="https://static.vecteezy.com/system/resources/previews/001/886/209/non_2x/doctor-medical-cartoon-design-vector.jpg" img-alt="Card image" img-right img-height="500">
      <b-card-text>
        <div>
  <b-form >
    <label for="inline-form-input-name">Id</label>
    <b-form-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="Id"
    ></b-form-input>
    <br>
    <label for="inline-form-input-name">Id de Empleado</label>
    <b-form-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="Id de Empleado"
    ></b-form-input>
    <br>
    <label for="inline-form-input-name">Función</label>
    <b-form-input
      id="inline-form-input-name"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Función"
    ></b-form-input>
    <br>
    <label for="inline-form-input-name">Experiencia</label>
    <b-form-input
      id="inline-form-input-name"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Experiencia"
    ></b-form-input>
    <br>

    <b-button variant="primary">Guardar</b-button>
  </b-form>
</div>
      </b-card-text>
    </b-card>
    </div>
</template>

<script>
export default {
    name: 'IngresarDoctor'
}
</script>