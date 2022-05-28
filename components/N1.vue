<template>
  <div class="pretrazos3">
    <div id="pantalla1" class="pretrazos3_figura">
     <div v-bind:class="cargar_fig_geometrica.tipofigura">
     </div>      
    </div>

    <div id="pantalla2" class= "pretrazos3_responder" style="display:none;" >
      <div class="tiempo_bar">
        <div class="progress progresotime">
          <div class="progress-bar" role="progressbar" v-bind:style="'width:'+llenado_bar+'%'" aria-valuemin="0" aria-valuemax="100"></div>
        </div>
      </div>

      <div class="pretrazos3_responder-imagen">
        <div v-bind:class="cargar_fig_geometrica.tipofigura+'A'"></div>
      </div>

      <div class="pretrazos3_responder-opciones">
       
        <div class="opcion1" v-for="opciones in objcontenido.puntos" :key="opciones.length">
           <svg  class="figura1"  width="250px" height="200px">
             
            <path v-if="opciones.figop=='triangulo'" id="trazadoT" d="M35 169 L 135 20 L 228 169 H 35Z" fill="#EFF3FB" stroke="#858F98" stroke-width="5" stroke-dasharray="12 12"/>
            <rect v-if="opciones.figop=='cuadrado'" id="trazadoC" x="36" y="16" width="175" height="168" fill="#EFF3FB" stroke="#858F98" stroke-width="5" stroke-dasharray="12 12"/>
            <!-- <circle v-if="opciones.figop=='circulo'" id="trazadoCI" cx="127" cy="100" r="85" fill="#EFF3FB" stroke="#858F98" stroke-width="5" stroke-dasharray="12 12"/> -->
       
            <path v-if="opciones.figop=='circulo'" style="stroke: #858F98;stroke-width:5; fill: #EFF3FB; stroke-dasharray:12 12;" d="m43,100 a85,85 0 1, 0 0,-1 z"></path>
             
             <circle v-if="opciones.figop=='circulo'" id="indicador" display="none" r="10" style="fill: #ff0000;">								
             <animateMotion path="m210,100 a85,85 0 1, 1 0,-1 z" dur="10s" rotate="auto" repeatCount="indefinite" ></animateMotion>
             </circle> 

            <circle v-bind:cx="opciones.x" v-bind:cy="opciones.y" r="10" stroke="black" stroke-width="3" fill="black" /> 
            <circle v-bind:cx="opciones.x" v-bind:cy="opciones.y" r="10" stroke="blue" stroke-width="3" fill="black" /> 
          
          </svg> 
         <canvas  v-if="opciones.figop=='triangulo'" v-bind:id="opciones.figop" class="cva" width="250px" height="200px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas>  
         <canvas  v-if="opciones.figop=='cuadrado'"  v-bind:id="opciones.figop" class="cva" width="250px" height="200px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas>
         <canvas  v-if="opciones.figop=='circulo'"   v-bind:id="opciones.figop" class="cva" width="250px" height="200px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas> 
        </div> 
      </div>
    </div> 
  </div>
</template>

<script >
// import timer from '@/components/Progress.vue'
export default {
  name: 'HelloWorld',
  //  components: {
    // nivel1
    // timer
    // ...
  // },
  props: {
    plantilla_actual: String
  },
   data: function(){
    return{
      mostrar:true,
      myElement:"",
      canvas:null,
      context:null,
      isDrawing:false,
      
      
      
      
      mi_fin_llave1:0,
      captureToggle: false,
      inicie_ok:true,
      como_iniciaste:true,
      autox:0,
      autoy:0,
      auto_pocicion:0,

      //variables usadas
      mi_ini_llave1:false,
      objcontenido:{tipofigura:"circulo"},
      llave_direccion:false,
      llave_finalizar:false,
      llave_figura_correcta:false,
      evaluacion_unica:false,
      llave_inicio_correcto:null,
      click_figura_correcta:false,
      startXC:0,
      startYC:0,
      startXT:0,
      startYT:0,
      startXR:0,
      startYR:0,
      llave_punto_inicial:false,
      inicie_enelpunto:true,
      calificando:false,
      valorparar:null,
      inidibujarauto:null,
      tiempo_mm: 1000/90000,
      llenado_bar:0,
      milisegundos:0,
      segundos:0,
      
    }
  },
  computed: {
    cargar_fig_geometrica:function(){
    var contenidoquemado =  this.obtenercontenido()
    return contenidoquemado
       
    },
     mostrarvista2: function(){
      return false
    }
  
  },
  mounted(){
     this.cargar_figura();
   },
   methods:{
  
     obtenercontenido(){
        var random_llena= Math.ceil(Math.random()*3);
          // var random_llena= 3; 
          if(random_llena==1){  
            this.objcontenido={
            tipofigura:"cuadrado",
            direccion:"panright",
            inicio:[{x:36,y:16}],
            final:[{x:36,y:16}],
            puntos:[{figop:"cuadrado",direccion:"pandown",x:36,y:16},{figop:"triangulo",direccion:"panright",x:138,y:20},{figop:"circulo",direccion:"panleft",x:127,y:12}],
            rutacorrecta:[{x:36,y:16},{x:208,y:16},{x:208,y:182},{x:36,y:182},{x:36,y:16}],
          }
        }
        if(random_llena==2){  
            this.objcontenido={
            tipofigura:"triangulo",
            direccion:"panright",
            inicio:[{x:138,y:20}],
            final:[{x:138,y:20}],
            puntos:[{figop:"circulo",direccion:"panright",x:127,y:11},{figop:"cuadrado",direccion:"panright",x:36,y:16},{figop:"triangulo",direccion:"panright",x:138,y:20}],
            rutacorrecta:[{x:138,y:20},{x:225,y:300}],
          }
        }
        if(random_llena==3){  
            this.objcontenido={
            tipofigura:"circulo",
            inicio:[{x:127,y:11}],
            final:[{x:127,y:11}],
            direccion:"panright",
            puntos:[{figop:"circulo",direccion:"panright",x:127,y:11},{figop:"cuadrado",direccion:"panright",x:36,y:16},{figop:"triangulo",direccion:"panleft",x:138,y:20}],
            rutacorrecta:[{x:36,y:16},{x:208,y:16},{x:208,y:182},{x:36,y:182},{x:36,y:16}],
          }
        }
        for (let j = 0; j < this.objcontenido.puntos.length; j++) {
          if(this.objcontenido.puntos[j].figop=='cuadrado'){
          this.startXC=this.objcontenido.puntos[j].x
          this.startYC=this.objcontenido.puntos[j].y
          }
          if(this.objcontenido.puntos[j].figop=='triangulo'){
          this.startXT=this.objcontenido.puntos[j].x
          this.startYT=this.objcontenido.puntos[j].y
          }
          if(this.objcontenido.puntos[j].figop=='circulo'){
          this.startXR=this.objcontenido.puntos[j].x
          this.startYR=this.objcontenido.puntos[j].y
          }
        }
        return this.objcontenido
     },
    figura_correcta(valor){

      this.llave_figura_correcta=true;
       if(valor===this.objcontenido.tipofigura){
         this.click_figura_correcta=true;
         

       }else{         
         this.click_figura_correcta=false;
          document.getElementById("pantallaActividad").style.backgroundColor='#F6535DCC';
         setTimeout(() => {
           document.getElementById("pantallaActividad").style.backgroundColor='white';
           this.limpiar_trazo(valor)
           this.responder()
         },500);
       }
       return this.click_figura_correcta
     },
    automatico(){
    
      this.inidibujarauto= setInterval(  
        this.generar_ruta
      ,10);
    },
    generar_ruta(){
        
      
      if(this.autox != this.objcontenido.rutacorrecta[this.auto_pocicion+1].x){
        
        if(this.autox > this.objcontenido.rutacorrecta[this.auto_pocicion+1].x){
        this.autox=this.autox-1
      }else{this.autox=this.autox+1}
      }
      if(this.autoy != this.objcontenido.rutacorrecta[this.auto_pocicion+1].y){
         
         if(this.autoy > this.objcontenido.rutacorrecta[this.auto_pocicion+1].y){
        this.autoy=this.autoy-1
         }else{this.autoy=this.autoy+1}
      }
      
      
      if(this.autox==this.objcontenido.rutacorrecta[this.auto_pocicion+1].x & this.autoy==this.objcontenido.rutacorrecta[this.auto_pocicion+1].y){
        // clearInterval(this.inidibujarauto);
        console.log("asigne valor nuevo")
        
          this.auto_pocicion=this.auto_pocicion+1
          this.autox=this.objcontenido.rutacorrecta[this.auto_pocicion].x
          this.autoy=this.objcontenido.rutacorrecta[this.auto_pocicion].y
        if(this.auto_pocicion===this.objcontenido.rutacorrecta.length-1){
       
          clearInterval(this.inidibujarauto);
        }

      }
      
      
      console.log("me muevo")
      
     

      // console.log(this.autox,)     

     },
     // valida la direccion en la que incio independientemente que caja sea
     direccion(direccion_capturada,figura){
       this.evaluacion_unica=true;
       console.log(direccion_capturada,figura)
       for (let i = 0; i < this.objcontenido.puntos.length; i++) {
          if(this.objcontenido.tipofigura===figura & direccion_capturada===this.objcontenido.direccion){
             this.llave_direccion=true
          }
       }
       if(this.llave_direccion==false){
         this.llave_direccion=false
        //  document.getElementById("pantallaActividad").style.backgroundColor='#F6535DCC';
       }
     },
     limpiar_trazo(value){
       console.log(value)
       var canvas = this.canvas;
       var ctx = canvas.getContext("2d");
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        this.startX=this.caminoX;
        this.startY=this.caminoY;
     },
     cargar_figura(){
        this.llenado_bar=0
      this.milisegundos=0
      this.segundos=0
      //  console.log(this.objcontenido);
        setTimeout(() => {
            document.getElementById('pantalla1').style.display='none'; 
            this.mostrar=this.mostrarvista2;
            console.log("aqui debo moostrar el tiempo")
             this.iniciando();
            document.getElementById('pantalla2').style.display='block'; 
            this.autox=this.objcontenido.rutacorrecta[0].x;
            this.autoy=this.objcontenido.rutacorrecta[0].y;
            // this.$emit("mostrartime",true);
         },5000);  
     },
     responder(){
       this.parar_tiempo();

       this.llave_finalizar=true;

       if(this.calificando==false){
        //  this.parar_tiempo();
         if(this.llave_direccion==true & this.click_figura_correcta==true & this.inicie_enelpunto==true){
           this.$emit("respuestasalumno",true);
         }else{
           this.limpiar_trazo()
           document.getElementById('indicador').style.display='block';                   
          //  this.automatico()
           this.$emit("respuestasalumno",false); 
         }
         
       }
       this.calificando=true
     },
     trazar(clientX,clientY,estoyen){ 
      
       this.canvas = document.getElementById(estoyen);      
       this.context=this.canvas.getContext("2d");
       var rect = this.canvas.getBoundingClientRect();
       var x=clientX-rect.left;
       var y=clientY-rect.top;
       var startX;
       var startY;
     
       if(estoyen=="cuadrado"){
         startX=this.startXC
         startY=this.startYC
       }
      if(estoyen=="circulo"){
         startX=this.startXR
         startY=this.startYR
       }
      if(estoyen=="triangulo"){
         startX=this.startXT
         startY=this.startYT
       }
      // console.log(parseInt(x),parseInt(y))
      if(this.llave_punto_inicial==false){
        // console.log(parseInt(x),parseInt(y))
        setTimeout(() => {
          this.mi_ini_llave1=true
         },3000);
        if(x<(this.objcontenido.inicio[0].x+20) & y<(this.objcontenido.inicio[0].y+10))
        {
         this.inicie_enelpunto=true
         this.llave_punto_inicial=true
         console.log("vas bien")
        } 
        // if(x>(this.objcontenido.inicio[0].x+20) & y>(this.objcontenido.inicio[0].y)){
        else{console.log("vas mal")
         this.inicie_enelpunto=false
         this.llave_punto_inicial=true
         startX=x
         startY=y
         
        }
       } 
      
      if(this.isDrawing){ 
      
        if(x>=this.objcontenido.final[0].x-10 & x<=this.objcontenido.final[0].x+10 & y>=this.objcontenido.final[0].y-10 & y<=this.objcontenido.final[0].y){
          if(this.mi_ini_llave1==true){
           this.responder() 

            
            // console.log(this.obtener)
          }
          
        }

         console.log(x,y)   
        
        this.context.beginPath();
        this.context.moveTo(startX,startY);
        this.context.lineTo(x,y);
        this.context.lineWidth=8;
        this.context.lineCap ='round';
        this.context.strokeStyle ="#4978D6";
        this.context.stroke();
      
     
     if(estoyen=="cuadrado"){
         this.startXC=x
         this.startYC=y
       }
      if(estoyen=="circulo"){
         this.startXR=x
         this.startYR=y
       }
      if(estoyen=="triangulo"){
         this.startXT=x
         this.startYT=y
       }
        // this.startX=x;
        // this.startY=y;    
      }
      
    },
     mo: function(e) {

      if (this.captureToggle==true & this.llave_finalizar==false) {
      var dondeestoy= e.target.id  
      var x= e.center.x;
      var y= e.center.y;
      var figura_clikeada= this.llave_figura_correcta==false?this.figura_correcta(dondeestoy):true;
      
      if(figura_clikeada){
      // console.log(e.additionalEvent)
      if(this.llave_direccion===false & this.evaluacion_unica===false){
       if(e.additionalEvent=="panleft" | e.additionalEvent=="panright"){
         this.direccion(e.additionalEvent,dondeestoy)
        console.log(this.llave_direccion)
       }
      }
      this.trazar(x,y,dondeestoy)
      }
      // else{
      //   console.log(dondeestoy,x,y)
      // }
     }
    },
     captureOn: function() {
      //  if(this.llave==1 & this.colision==false & this.llave_fin==0){
      // console.log(this.captureToggle)  
      this.captureToggle = true
      this.isDrawing=true
      // }
    },
     captureOff: function() {
      this.captureToggle = false
      // console.log(this.captureToggle)
       this.isDrawing=false;
    },
    iniciando(){
   this.valorparar = setInterval(
   this.iniciar_tiempo
        
      ,10);
    },
    iniciar_tiempo(){
    
   this.milisegundos++;
   this.llenado_bar=this.llenado_bar+this.tiempo_mm;

  //  console.log(this.llenado_bar);
    if(this.milisegundos==100){
      this.milisegundos=0;
      this.segundos++;
      // console.log(this.segundos)
     
    }
    if(this.segundos===91){
              this.parar_tiempo()
              this.$emit("tiempo",false);
              document.getElementById("pantallaActividad").style.backgroundColor='#F6535DCC';
    }         
    },
    parar_tiempo(){
      clearInterval(this.valorparar);
    },
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
.pretrazos3_figura{
  // outline: 2px solid red;
  display: flex;
  justify-content: center;
  padding-top: 30px;
  height: 100%;
  width: 100%;
}
.pretrazos3_responder{
  // outline: 2px solid red;
 
  height: 100%;
  width: 100%;
}
.pretrazos3_responder-imagen{
  // outline: 2px solid blue;
  width: 80%;
  height: 225px;
  display: flex;
  flex-direction: column;
    /* justify-content: center; */
  align-items: center;
  margin: 0 auto;
      border-bottom: 8px solid #FFCC0D;

}.pretrazos3_responder-opciones{
  // outline: 2px solid green;
    width: 100%;
    height: 220px;
    display: flex;
}
.linea{
 height: 9px;
 width: 72%;
 background: #FFCC0D;
 margin: 4px;
}
.image{
  height: 207px;
}
.opcion1{
    // outline: solid 2px red;
    width: 250px;
    height: 200px;
    margin: auto;
}
.figura1{
  position: absolute;
  margin: auto;
}
.cva{
  // outline: 2px solid magenta;
  position: relative;
}



.triangulo{
  width: 100px;
  height: 100px;
  border-top: solid transparent 0px;
  border-left: solid transparent 180px;
  border-right:solid transparent 180px;
  border-bottom: solid #FF96C9 350px;
}
.circulo{
  width: 420px;
  height: 420px;
  border-radius: 100%;
  background-color: #804DD7;
  // border-bottom: solid green 350px;
}
.circuloA{
  width: 210px;
  height: 210px;
  border-radius: 100%;
  background-color: #804DD7;
  margin: 5;
  // border-bottom: solid green 350px;
}
.cuadrado{
  width: 420px;
  height: 420px;
  background-color: #FFCC0D;
}
.cuadradoA{
  width: 200px;
  height: 200px;
  background-color: #FFCC0D;
  margin: 5px;
}
.trianguloA{
  border-top: solid transparent 0px;
  border-left: solid transparent 100px;
  border-right:solid transparent 100px;
  border-bottom: solid #FF96C9 203px;
}
.RectanguloA {
   width: 200px;
   height: 100px;
   background: #08B;
}
.OvaloA {
  margin: 45px;
border-radius:50%;
width: 210px;
height: 226px;
background: #08B;
}
.RomboA {
     width: 100px; 
     height: 100px; 
     background: black;
     -webkit-transform: rotate(45deg);
     -moz-transform: rotate(45deg);
     -ms-transform: rotate(45deg);
     -o-transform: rotate(45deg);
     transform: rotate(45deg);
}
.CorazonA {
  background-color: red;
  display: inline-block;
  height: 50px;
  margin: 0 10px;
  top: 0;
  transform: rotate(-45deg);
  position: absolute; 
  left: 45%; 
  top: 45%;
  width: 50px;
}
.Rectangulo {
   width: 300px;
   height: 150px;
   background: #08B;
}
.Ovalo {
border-radius:50%;
width: 200px;
height: 100px;
background: #08B;
}
.Rombo {
     width: 100px; 
     height: 100px; 
     background: black;
     -webkit-transform: rotate(45deg);
     -moz-transform: rotate(45deg);
     -ms-transform: rotate(45deg);
     -o-transform: rotate(45deg);
     transform: rotate(45deg);
}
.Corazon {
  background-color: red;
  display: inline-block;
  height: 50px;
  margin: 0 10px;
  top: 0;
  transform: rotate(-45deg);
  position: absolute; 
  left: 45%; 
  top: 45%;
  width: 50px;
}

</style>
