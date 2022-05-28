<template>
  <div class="pretrazos3">
    <div id="pantalla1" class="pretrazos3_figura">
     <div class="Rectangulo">
         <svg width="800px" height="450px" class="figura1">
            
         <circle v-if="cargar_fig_geometrica.tipofigura=='circulo'" v-bind:id="cargar_fig_geometrica.tipofigura" x="20" y="20" cx="400" cy="225" r="210" fill="#804DD7"/>
         <polygon v-if="cargar_fig_geometrica.tipofigura=='triangulo'" v-bind:id="cargar_fig_geometrica.tipofigura" points="400,25 200,400 600,400" fill="#FF96C9"/>
         <rect v-if="cargar_fig_geometrica.tipofigura=='cuadrado'" v-bind:id="cargar_fig_geometrica.tipofigura" x="200" y="20" width="435" height="410" fill="#FFCC0D"/>
         <rect v-if="cargar_fig_geometrica.tipofigura=='Rectangulo'" v-bind:id="cargar_fig_geometrica.tipofigura" x="20" y="80" width="760" height="280" fill="#0832B5"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='Corazon'" v-bind:id="cargar_fig_geometrica.tipofigura" x="20" y="20" d="M114.75 0C51.3851 0 0 50.8225 0 113.525C0 164.141 20.0813 284.271 217.75 405.708C221.29 407.861 225.355 409 229.5 409C233.645 409 237.71 407.861 241.25 405.708C438.919 284.271 459 164.141 459 113.525C459 50.8225 407.615 0 344.25 0C280.885 0 229.5 68.803 229.5 68.803C229.5 68.803 178.115 0 114.75 0Z" fill="#FF8001"/>
         <polygon v-if="cargar_fig_geometrica.tipofigura=='Trapecio'" v-bind:id="cargar_fig_geometrica.tipofigura" points="300,50 500,50 600,400 200,400" fill="#00987E"/>
         <polygon v-if="cargar_fig_geometrica.tipofigura=='Rombo'" v-bind:id="cargar_fig_geometrica.tipofigura" points="400,25 600,215 400,400 200,215" fill="#87A3FA"/>
         <ellipse v-if="cargar_fig_geometrica.tipofigura=='Ovalo'" v-bind:id="cargar_fig_geometrica.tipofigura" cx="400" cy="225" rx="333.5" ry="190" fill="#804DD7"/>
         

         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferencia'" style="display:none;" id="circunferencia" xlink:href="@/assets/leftc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 
         
         </svg>
        
       <canvas ref="canvas" v-bind:id="cargar_fig_geometrica.tipofigura" class="cva" width="800px" height="450px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas>
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
      llave_finalizar:true,
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
        var random_llena= Math.ceil(Math.random()*8);
          // var random_llena= 20; 
        if(random_llena==1){  
            this.objcontenido={
            tipofigura:"cuadrado",
            direccion:"pandown",//esta es la direccion correcta
            inicio:[{x:200,y:20}],
            final:[{x:200,y:20}],
            puntos:[{figop:"cuadrado",direccion:"pandown",x:200,y:20,img:"rectan"}],
  
          }
        }
        if(random_llena==2){  
            this.objcontenido={
            tipofigura:"triangulo",
            direccion:"panright",
            inicio:[{x:400,y:25}],
            final:[{x:400,y:25}],
            puntos:[{figop:"circulo",direccion:"panright",x:400,y:25,img:"poligonosinv"}],
          }
        }
        if(random_llena==3){  
            this.objcontenido={
            tipofigura:"circulo",
            inicio:[{x:400,y:16}],
            final:[{x:400,y:16}],
            direccion:"panright",
            puntos:[{figop:"circulo",direccion:"panright",x:400,y:16,img:"circunferenciainv"}],
          }
        }
        if(random_llena==4){  
            this.objcontenido={
            tipofigura:"Rectangulo",
            inicio:[{x:20,y:80}],
            final:[{x:20,y:80}],
            direccion:"panright",
            puntos:[{figop:"Rectangulo",direccion:"panright",x:20,y:80,img:"rectaninv"}],
          }
        }
        if(random_llena==5){  
            this.objcontenido={
            tipofigura:"Corazon",
            inicio:[{x:25,y:25}],
            final:[{x:25,y:25}],
            direccion:"panright",
            puntos:[{figop:"Corazon",direccion:"panright",x:25,y:25,img:"poligonosinv"}],
          }
        }
        if(random_llena==6){  
            this.objcontenido={
            tipofigura:"Trapecio",
            inicio:[{x:300,y:50}],
            final:[{x:300,y:50}],
            direccion:"panright",
            puntos:[{figop:"Trapecio",direccion:"panright",x:300,y:50,img:"rectaninv"}],
          }
        }
        if(random_llena==7){  
            this.objcontenido={
            tipofigura:"Ovalo",
            inicio:[{x:400,y:35}],
            final:[{x:400,y:35}],
            direccion:"panleft",
            puntos:[{figop:"Ovalo",direccion:"panleft",x:400,y:35,img:"circunferencia"}],
          }
        }
        if(random_llena==8){  
            this.objcontenido={
            tipofigura:"Rombo",
            inicio:[{x:400,y:25}],
            final:[{x:400,y:25}],
            direccion:"panright",
            puntos:[{figop:"Rombo",direccion:"panright",x:400,y:25,img:"poligonosinv"}],
          }
        }
        for (let j = 0; j < this.objcontenido.puntos.length; j++) {
          this.startXC=this.objcontenido.puntos[j].x
          this.startYC=this.objcontenido.puntos[j].y
        }
        return this.objcontenido
     },
    figura_correcta(valor){

      this.llave_figura_correcta=true;
     
     if(valor===this.objcontenido.tipofigura){
         this.click_figura_correcta=true;  
       }else{         
         this.click_figura_correcta=true;
       }
       return this.click_figura_correcta
     },
     // valida la direccion en la que incio independientemente que figura sea
     direccion(direccion_capturada, figura){
       this.evaluacion_unica=true;

      console.log(figura)
       for (let i = 0; i < this.objcontenido.puntos.length; i++) {
         if(figura==="cuadrado" | figura ==="rectangulo" | figura==="Trapecio"){
          if(direccion_capturada=="pandown" | direccion_capturada=="panright"){
            if(direccion_capturada===this.objcontenido.direccion){
             this.llave_direccion=true
            }
          }
         }else{
           if(figura==="triangulo"){
             this.evaluacion_unica=false;
              if(direccion_capturada===this.objcontenido.direccion){
              this.llave_direccion=true
              this.evaluacion_unica=true;
              }
           }
           if(direccion_capturada===this.objcontenido.direccion){
             this.llave_direccion=true
          }
         }
          
       }
       if(this.llave_direccion==false){
         this.llave_direccion=false
        //  document.getElementById("pantallaActividad").style.backgroundColor='#F6535DCC';
       }
       console.log("llave direccion:"+this.llave_direccion)
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
       console.log(this.objcontenido);
        setTimeout(() => {
          this.$emit("tiemporespuestas",true); 
           document.getElementById(this.objcontenido.tipofigura).style="stroke: #858F98;stroke-width:5; fill: #EFF3FB; stroke-dasharray:12 12;"
           document.getElementById('pinicio').style.display='block'
           document.getElementById('circunferencia').style.display='block'
            this.llave_finalizar=false
            this.mostrar=this.mostrarvista2;
            // console.log("aqui debo moostrar el tiempo")
            //  this.iniciando()
            // this.autox=this.objcontenido.rutacorrecta[0].x;
            // this.autoy=this.objcontenido.rutacorrecta[0].y;
            // this.$emit("mostrartime",true);
         },5000);  
     },
     responder(){
       
this.$emit("tiemporespuestas",false); 
       this.llave_finalizar=true;

       if(this.calificando==false){
        //  this.parar_tiempo();
         if(this.llave_direccion==true & this.click_figura_correcta==true & this.inicie_enelpunto==true){
           this.$emit("respuestasalumno",true);
         }else{
           this.limpiar_trazo()
          //  document.getElementById('indicador').style.display='block';                   
          //  this.automatico()
           this.$emit("respuestasalumno",false); 
         }
         
       }
       this.calificando=true
     },
     trazar(clientX,clientY){ 
       
      this.canvas =this.$refs.canvas  
       this.context=this.canvas.getContext("2d");
       var rect = this.canvas.getBoundingClientRect();
       var x=clientX-rect.left;
       var y=clientY-rect.top;
       var startX;
       var startY;
         startX=this.startXC
         startY=this.startYC
    
      if(this.llave_punto_inicial==false){
        
        setTimeout(() => {
          this.mi_ini_llave1=true
         },3000);

        if(x<(this.objcontenido.inicio[0].x+20) & y<(this.objcontenido.inicio[0].y+20))
        {
         this.inicie_enelpunto=true
         this.llave_punto_inicial=true
         console.log("iniciaste bien")
        } 
        if(x>(this.objcontenido.inicio[0].x+20) & y>(this.objcontenido.inicio[0].y+20)){
      
         this.inicie_enelpunto=false
         this.llave_punto_inicial=true
         startX=x
         startY=y
         console.log("iniciaste mal")
        }
       } 
      
      if(this.isDrawing){ 
       
        if(x>=this.objcontenido.final[0].x-10 & x<=this.objcontenido.final[0].x+10 & y>=this.objcontenido.final[0].y-10 & y<=this.objcontenido.final[0].y){
          if(this.mi_ini_llave1==true){
           this.responder() 
           
          }
          
        }

        //  console.log(x,y)   
        this.context.beginPath();
        this.context.moveTo(startX,startY);
        this.context.lineTo(x,y);
        this.context.lineWidth=8;
        this.context.lineCap ='round';
        this.context.strokeStyle ="#4978D6";
        this.context.stroke();
         this.startXC=x
         this.startYC=y
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
      //  console.log(dondeestoy)
      if(this.llave_direccion===false & this.evaluacion_unica===false){
   
         this.direccion(e.additionalEvent,dondeestoy)
      
      }
      // console.log(dondeestoy,x,y)
      this.trazar(x,y)
      }
      // else{
        // console.log(dondeestoy,x,y)
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
  .pretrazos3{
    height: 100%;
    width: 100%;
  }
.pretrazos3_figura{
  // outline: 2px solid red;
  display: flex;
  justify-content: center;
  // padding-top: 30px;
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
#manita{
  position: relative;
}

.Rectangulo {
      display: flex;
    justify-content: center;
    height: 450px;
    width: 830px;
}


</style>
