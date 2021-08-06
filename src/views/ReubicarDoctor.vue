<template>
    <div>
        <br><br><br>
       <b-card img-src="https://prints.ultracoloringpages.com/f5da751484fa8313f44617f030727404.png" img-alt="Card image" img-right img-height="500">
      <b-card-text>
        <div>
      <label for="inline-form-input-name">Seleccione el Doctor</label>
    <select v-model="id">
      <option value="">Escoge un doctor</option>
      <option v-for="(med,index) in listDr" :key=index  :value="med.id">{{med.id}}</option>
    </select>
    <b-button variant="primary" v-on:click="edit()">Cargar datos</b-button>
    <br>        
  <b-form>
    <label>Id empleado</label>
    <br>
    <input type="text" id="idE">
    <br>
    <label>Funcion</label>
    <br>
    <input type="text" id="funcion">
    <br>
    <label>Experiencia</label>
    <br>
    <input type="text" id="xp">
    <b-button variant="primary" v-on:click="update()">Guardar</b-button>
  </b-form>
</div>
      </b-card-text>
    </b-card>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'reubicarDoctor',
  data(){
    return {
      id: 0,
      listDr: '',
      editMed: {
        id_empleado: 0,
        funcion: '',
        experiencia: ''
      },
      updateMed:{
        id_empleado: 0,
        funcion: "",
        experiencia: ""
      }
    }
  },
  mounted(){
    this.listMed();
  },
  methods:{
    listMed(){
      axios.get("http://localhost:3900/api/listMed")
      .then(res => {
        this.listDr = res.data["medico"];
      })
      .catch(e=>console.log(e));
    },
    edit(){
      axios.get("http://localhost:3900/api/editMed/"+this.id)
      .then(res=>{
        if(res.status==200){
          this.editMed = res.data["medico"];
          document.getElementById("idE").value = this.editMed[0].id_empleado;
          document.getElementById("funcion").value = this.editMed[0].funcion;
          document.getElementById("xp").value = this.editMed[0].experiencia;
        }
      })
      .catch(e=>console.log(e));
    },
    update(){
      this.updateMed.id_empleado = parseInt(document.getElementById("idE").value);
      this.updateMed.funcion = document.getElementById("funcion").value;
      this.updateMed.experiencia = document.getElementById("xp").value;
      axios.put("http://localhost:3900/api/updateMed/"+this.id,this.updateMed)
      .then(res=>{
        if(res.status==200){
          this.updateMed = res.data["medico"];
          document.getElementById("idE").value = "";
          document.getElementById("funcion").value = "";
          document.getElementById("xp").value = "";
        }
      })
      .catch(e=>console.log(e));
    }
  }
}
</script>