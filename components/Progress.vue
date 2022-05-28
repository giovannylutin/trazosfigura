<template>
  <div class="tiempo_bar">
    <div class="progress progresotime">
      <div class="progress-bar" role="progressbar" v-bind:style="'width:'+llenado_bar+'%'" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
  </div>
</template>

<script >

export default {
  name: 'HelloWorld',
  props: {
    plantilla_actual: String
  },
   data: function(){
    return{
    valorparar:null,
    tiempo_mm: 1000/90000,
    llenado_bar:0,
    milisegundos:0,
    segundos:0
    }
  },
  computed: {
  },
  mounted(){
    
      this.iniciando();
   },
   methods:{
    
     // valida la direccion en la que incio independientemente que caja sea
  

   }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.tiempo_bar{
    display: flex;
    justify-content: center;
  }
  .progresotime{
    // margin-left: calc(50% - 25%);
    margin-top:10px ;
    width: 78%;
    height: 14px;
     border-radius: 20px;
     background: #ffd6ad;; 
  }
  .progress-bar{
  background-color:orange;
  }

</style>
