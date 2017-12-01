- <template>
  <div >
      
        <template v-for="(data,indice) in prueba.campos"> 
           {{prueba}}
           <input :type="data.type" :id="data.id" :max="data.max" :placeholder="data.placeholder" @keyup="Presiono(indice,data.value)" v-on:click="algo(indice)"  required>
        <br><br>
        </template>
      </form>
         {{objeto}}


  </div>
</template> 
<script>
import Form from './Form.vue'
export default {
  props: ['prueba'],  
  data () {
    
    return {
        prue: '',
        objeto: {
            uno:'',
            dos:'',
            tres: ''
        },
    }
  },
  methods: {
      actualizar(indice){
          console.log("")
      },
      Presiono(index,algo){
          
    
          setTimeout(function(){
       console.log("this.objeto."+this.prueba.campos[index].vmodel+"="+document.getElementById(this.prueba.campos[index].id).value)
            if(document.getElementById(this.prueba.campos[index].id).value==''){
            eval("this.objeto."+this.prueba.campos[index].vmodel+"= null");
            }else{
            eval("this.objeto."+this.prueba.campos[index].vmodel+"="+document.getElementById(this.prueba.campos[index].id).value);
            }
            }.bind(this))

        

            



        

      },

      algo(indice){
          console.log(indice)
         /*  this.objeto= this.prueba.propiedades
           var limpiar= '';
           this.prueba.propiedades.uno=limpiar
        console.log(this.prueba)
        this.limpiar=this.prueba.propiedades.uno=''
        console.log(this.objeto)*/
        }
  },

    update: function () {
        console.log("monantes de montad")
        
        
        //console.log(this.prueba.campos)
        //this.camposvmodel = this.prueba.campos
        //console.log(this.camposvmodel)
        
    },

}
</script>


<style>

</style>
