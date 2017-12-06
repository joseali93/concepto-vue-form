<template>
  <div id="app">
    
   <div>
      <form>
        <template v-for="(data,indice) in prueba"> 
      <input :type="data.type" :id="data.id" :max="data.max" :placeholder="data.placeholder" @keyup="Presiono(indice)"   required>
        </template>
      </form>
    </div>
  {{objeto}}
 
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
      prueba: [{
        type: 'number',
        min: '1',
        max: '99',
        placeholder: 'peso',
        id: 'numero',
        vmodel: 'uno'},
        

      ],
      objeto: {
        uno: ''
      }
    }
  },
  
  methods: {
   Presiono(index){
     console.log("entro")
         console.log(index) 
    
          setTimeout(function(){
            if(document.getElementById(this.prueba[index].id).value==''){
            eval("this.objeto."+this.prueba[index].vmodel+"= null");
            }else{
            eval("this.objeto."+this.prueba[index].vmodel+"="+document.getElementById(this.prueba[index].id).value);
            }
            }.bind(this))
      },
  }
}
</script>   

<style>

</style>
