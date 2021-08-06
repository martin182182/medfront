<template>
    <div>
        <br><br><br>
       <b-card img-src="https://www.popularenlinea.com/SiteCollectionImages/personas/joven/Articulos/Diciembre/Imagen-Blog.png" img-alt="Card image" img-right img-height="500">
      <b-card-text>
          
        <div>
  <b-form >
    <label for="inline-form-input-name">Seleccione el doctor</label>
    <select id="med">
      <option value="">Escoge un empleado</option>
      <option v-for="(med,index) in listMed" :key=index  :value="[med.id_centro,med.id_empleado]">{{med.nombre}}</option>
    </select>
    <br>
    <b-button variant="primary" id="btnGenerarNomina" v-on:click="save()">Generar nómina</b-button>
    <br>
    <div id="nomina">
        
    </div>
    <br>
    <b-button variant="primary" v-on:click="reportPDF()">Guardar como PDF</b-button>
  </b-form>
</div>
      </b-card-text>
    </b-card>
    </div>
</template>

<script>
import axios from 'axios';
import jspdf from 'jspdf';
import jsPDF from 'jspdf';
export default {
  name: 'nominaPago',
  mounted(){
    this.listMedCenter()
  },
  data(){
    return {
      listMed: '',
      med: '',
      report: new jsPDF()
    }
  },
  methods:{
    listMedCenter(){
      axios.get("http://20.84.120.37:3000/api/listMedCenter")
      .then(res=>{
        this.listMed = res.data["medico"];
      })
      .catch(e=>console.log(e));
    },
    save(){
      var id = document.getElementById("med").value;
      var idSplit = id.split(",");
      console.log(idSplit);
      axios.get("https://obscure-ridge-32684.herokuapp.com/api/v1/consulta/"+idSplit[0]+"/"+idSplit[1]+"/empleado")
      .then(res=>{
        this.med = res.data;
      })
      .catch(e=>console.log(e));
    },
    reportPDF(){
      var space = 1;
      for(let i = 0; i< this.med.length;i++){
        this.report.text(20,(i*20)+20,this.med[i].id.toString()+"\n");
      }
      this.report.save("test.pdf");
    }
  }
}
</script>