<template>
    <div>
        <br><br><br>
       <b-card img-src="https://static.vecteezy.com/system/resources/previews/001/886/209/non_2x/doctor-medical-cartoon-design-vector.jpg" img-alt="Card image" img-right img-height="500">
      <b-card-text>
        <div>
  <b-form >
    <label for="inline-form-input-id">Id de Empleado</label>
    <select id="employee" v-model="med.id_empleado">
      <option value="">Escoge un empleado</option>
      <option v-for="(employee,index) in listEmployee" :key=index  :value="employee.id">{{employee.nombre}}</option>
    </select>
    <br>
    <label for="inline-form-input-function">Función</label>
    <b-form-input
      id="inline-form-input-function"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Función"
      v-model="med.funcion"
    ></b-form-input>
    <br>
    <label for="inline-form-input-xp">Experiencia</label>
    <b-form-input
      id="inline-form-input-xp"
      class="mb-1 mr-sm-1 mb-sm-0"
      placeholder="Experiencia"
      v-model="med.experiencia"
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
  name: 'IngresarDoctor',
  data(){
    return {
      listEmployee: '',
      med: {
        id_empleado: 0,
        funcion: '',
        experiencia: ''
      }
    }
  },
  mounted(){
    this.list();
  },
  methods:{
    list(){
      axios.get("http://localhost:3900/api/listEmployee")
      .then(res=>{
        if(res.status==200){
          this.listEmployee = res.data["empleado"];
        }
      })
      .catch(e=>console.log(e));
    },
    save(){
      axios.post("http://localhost:3900/api/createMed",this.med)
      .then(res=>{
        if(res.status==200){
          alert('Empleado '+this.med.id_empleado+' es doctor/a');
          this.med = res.data;
        }
      });
    }
  }
}
</script>