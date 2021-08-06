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
      v-model="employee.nombre" 
    ></b-form-input>
    <br>
    <label for="inline-form-input-dir">Dirección</label>
    <b-form-input
      id="inline-form-input-dir"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="Dirección"
      v-model="employee.direccion" 
    ></b-form-input>
    <br>
    <label for="inline-form-input-salary">Salario</label>
    <b-form-input
      id="inline-form-input-salary"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Salario"
      v-model="employee.salario" 
    ></b-form-input>
    <br>
    <label for="example-datepicker">Fecha de entrada</label>
    <b-form-datepicker id="example-datepicker" v-model="employee.fecha_entrada" class="mb-2"></b-form-datepicker>
    <br>
    <select id="center" v-model="employee.id_centro">
      <option value="">Escoge un centro</option>
      <option v-for="(center,index) in listCenter" :key=index  :value="center.id">{{center.nombre}}</option>
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
      listCenter: '',
      employee: {
        nombre: '',
        salario: '',
        direccion: '',
        fecha_entrada: '',
        id_centro: ''

      }
    }
  },
  mounted(){
    this.list();
  },
  methods:{
    list(){
      axios.get("http://localhost:3900/api/listCenter")
      .then(res=>{
        this.listCenter=res.data["centro"];
      })
      .catch(e=>console.log(e));
    },
    save(){
      axios.post("http://localhost:3900/api/createEmployee",this.employee)
      .then(res=>{
        if(res.status==200){
          alert(this.employee.nombre+' se guardo con exito');
          this.employee = res.data;
        }
      })
      .catch(e=>alert('Error al guardar'))
    }
  }
}
</script>