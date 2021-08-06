<template>
    <div>
        <br><br><br>
       <b-card img-src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQmf-LkcfXUGwwlJuY3i-OJKjGx7pWFC849Ng&usqp=CAU" img-alt="Card image" img-right img-height="500">
      <b-card-text>
        <div>
  <b-form >
    <label for="inline-form-input-name">Nombre</label>
    <b-form-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="Nombre"
    ></b-form-input>
    <br>
    <label for="inline-form-input-dir">Dirección</label>
    <b-form-input
      id="inline-form-input-dir"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="Dirección"
    ></b-form-input>
    <br>
    <label for="inline-form-input-salary">Salario</label>
    <b-form-input
      id="inline-form-input-salary"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Salario"
    ></b-form-input>
    <br>
    <label for="example-datepicker">Fecha de entrada</label>
    <b-form-datepicker id="example-datepicker" class="mb-2"></b-form-datepicker>
    <br>
    <select id="center">
      <option v-for="(center,index) in listCenter" :key=index :value="center.id">{{center.nombre}}</option>
    </select>
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
  name: 'IngresarEmpleado',
  data(){
    return {
      listCenter: ''
    }
  },
  mounted(){
    this.list();
  },
  methods:{
    list(){
      axios.get("http://localhost:3000/api/listCenter")
      .then(res=>{
        this.listCenter=res.data["centro"];
      })
      .catch(e=>console.log(e));
    },
    save(){
      var selectCenter = document.getElementById("center").value;
      console.log(selectCenter);
    }
  }
}
</script>