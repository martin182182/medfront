<template>
    <div>
        <br><br><br>
       <b-card img-src="https://www.popularenlinea.com/SiteCollectionImages/personas/joven/Articulos/Diciembre/Imagen-Blog.png" img-alt="Card image" img-right img-height="500">
      <b-card-text>
          
        <div>
  <b-form >
    <label for="inline-form-input-name">Seleccione el doctor</label>
    <div>
        <b-dropdown id="dDoctor" text="Seleccione el doctor" class="m-md-2">
        </b-dropdown>
    </div>
    <br>
    <b-button variant="primary" id="btnGenerarNomina">Generar nómina</b-button>
    <br>
    <div id="nomina">
        
    </div>
    <br>
    <b-button variant="primary" id="btnGuardarPDF">Guardar como PDF</b-button>
  </b-form>
</div>
      </b-card-text>
    </b-card>
    </div>
</template>

<script>
export default {
    name: 'nominaPago'
}
</script>