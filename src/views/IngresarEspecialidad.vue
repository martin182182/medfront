<template>
    <div>
        <br><br><br>
       <b-card img-src="https://st2.depositphotos.com/1663905/10044/v/600/depositphotos_100448476-stock-illustration-medical-health-care-specialties-icons.jpg" img-alt="Card image" img-right img-height="500">
      <b-card-text>
        <div>
  <b-form >
    <label for="inline-form-input-name">Nombre</label>
    <b-form-input
      id="inline-form-input-name"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Nombre"
      v-model="specialty.nombre"
    ></b-form-input>
    <br>
    <label for="inline-form-input-descripcion">Descripción</label>
    <b-form-input
      id="inline-form-input-descripcion"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Descripción"
      v-model="specialty.descripcion"
    ></b-form-input>
    <br>

    <b-button variant="primary" v-on:click="save()">Guardar</b-button>
  </b-form>
</div>
      </b-card-text>
    </b-card>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'IngresarEspecialidad',
  data(){
    return {
      specialty:{
        nombre: "",
        descripcion: ""
      }
    }
  },
  methods:{
    save(){
      this.specialty.nombre = document.getElementById("inline-form-input-name").value;
      this.specialty.descripcion = document.getElementById("inline-form-input-descripcion").value;
      axios.post("http://localhost:3000/api/createSpecialty",this.specialty).then(res=>{
        if(res.status == 200){
          this.specialty = res.data;
        }
      }).catch(e=>console.log(e));
      this.specialty.nombre = "";
      this.specialty.descripcion = "";
    }
  }
}
</script>