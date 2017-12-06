- <template>
  <div >
      
        <template v-for="(data,indice) in prueba.campos"> 
           {{prueba}}
           <input :type="data.type" :id="data.id" :max="data.max" :placeholder="data.placeholder" @keyup="Presiono(indice,data.value)" v-on:click="algo(indice)"  required>
        <br><br>
        </template>
      </form>
      {{prueba}}
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
       console.log("this.objeto."+this.prueba.campos.vmodel+"="+document.getElementById(this.prueba.campos.id).value)
            if(document.getElementById(this.prueba.campos.id).value==''){
            eval("this.objeto."+this.prueba.campos.vmodel+"= null");
            }else{
            eval("this.objeto."+this.prueba.campos.vmodel+"="+document.getElementById(this.prueba.campos.id).value);
            }
            }.bind(this))
      },

  }

}
</script>


<style>

</style>
