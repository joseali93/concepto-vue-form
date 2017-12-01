<template>
  <div id="app">
    <select class="form-control" v-model="selectproduct" v-on:change="onChangeProd">
      <option value="" disabled>Productos</option>
      <option v-for="(data,indice) in productos" :value="data">{{data.nombre}}</option>         
    </select>
    <select class="form-control" v-model="selectservice" v-on:change="onChangeSer">
      <option value="" disabled>Servicios</option>
      <option v-for="(data,indice) in servicios" :value="data" >{{data.nombre}}</option>         
    </select>
   <!-- <div>
      <form>
        <template v-for="(data,indice) in prueba.campos"> 
           <input :type="data.type" :min="data.min" :max="data.max" :placeholder="data.placeholder" :value="data.value" required>

        </template>
      </form>
    </div>
    <div>
      {{selectproduct}}
      {{selectservice}}
    </div>-->
<prueba v-if="selectservice" v-bind:prueba="prueba"></prueba>
  </div>
</template>

<script>
import Prueba from './componentes/Form.vue'

export default {
    
  name: 'app',


  components: {
    Prueba
  },
  data () {
    return {
      selectservice: '',
      selectproduct: '',
      servicios: '',
      productos: '',
      prueba: ''
      
    }
  },
  render(createElement){
    console.log("entro render")

    return createElement(form,{

      props : {
         prueba: this.prueba
      },
      on: {
        save : function(){
            console.log("hola   mundo")
        }
      }
    })
    },
  methods: {
      onChangeProd:function(){
        console.log("producto")
        
         var url = 'http://192.168.1.69:3000/logistica/servicios/5a10ad88222f4a4183f20cc8';
          this.$http.get(url).then(respuesta =>{
          this.servicios=respuesta.body;
//          console.log(this.servicios)
            return (this.$http.get());
          }, (error) => console.log(error)); 
      },
      onChangeSer: function(){
        console.log("servicio")
        var idservicio = this.selectservice._id
        var idproducto = this.selectproduct._id
        var url = 'http://192.168.1.69:3000/logistica/estructuraf/'+idproducto+'/'+idservicio;
        this.$http.get(url).then(respuesta =>{
        this.prueba=respuesta.body
        console.log(respuesta)
        console.log(JSON.stringify(this.prueba))

        })
      }

  },
  beforeCreate: function () {
    
      console.log("funcion")
    
    console.log("antes crear")

 
    var url = 'http://192.168.1.69:3000/logistica/productos/5a2053336535d593c73c815e';
        this.$http.get(url).then(respuesta =>{
        this.productos=respuesta.body;
        })
        
    /*
    var url = 'http://192.168.1.82:3000/logistica/estructuraf/';
    this.$http.get(url).then(respuesta =>{
    this.prueba=respuesta.body;
    console.log(this.productos)
    })*/
  }
}
</script>   

<style>

</style>
