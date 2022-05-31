<template>
  <div class="pretrazos3">
    <div id="pantalla1" class="pretrazos3_figura">
     <div v-bind:class="cargar_fig_geometrica.tipofigura">
     </div>      
    </div>

    <div id="pantalla2" class= "pretrazos3_responder">
      <div class="pretrazos3_responder-imagen">
        <div v-bind:class="cargar_fig_geometrica.tipofigura+'A'"></div>
      </div>

      <div class="pretrazos3_responder-opciones">
       <div class="opcion1">
         <svg  width="250px" height="200px" class="figura1">
           <rect  v-bind:id="cargar_fig_geometrica.tipofigura" x="36" y="16" width="175" height="168" fill="#EFF3FB" stroke="#858F98" stroke-width="5" stroke-dasharray="12 12"/>
           <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="iz" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y"/>
           <circle display="none" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" />
         </svg>
         <canvas ref="canvascuadrado" v-if="this.objcontenido.puntos[0].figop=='cuadrado'"  v-bind:id="this.objcontenido.puntos[0].figop" class="cva" width="250px" height="200px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas>
       </div>

       <div class="opcion1">
         <svg  width="250px" height="200px" class="figura1">
            <path  v-bind:id="cargar_fig_geometrica.tipofigura" d="M35 169 L 135 20 L 228 169 H 35Z" fill="#EFF3FB" stroke="#858F98" stroke-width="5" stroke-dasharray="12 12"/>
           <!-- <rect v-if="cargar_fig_geometrica.tipofigura=='cuadrado'" v-bind:id="cargar_fig_geometrica.tipofigura" x="36" y="16" width="175" height="168" fill="#EFF3FB" stroke="#858F98" stroke-width="5" stroke-dasharray="12 12"/> -->
           <image v-if="cargar_fig_geometrica.puntos[1].img=='poligonos'" style="display:none;" id="izB" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[1].x-30" v-bind:y="objcontenido.puntos[1].y-20"/>
           <circle display="none" id="pinicioB" v-bind:cx="objcontenido.puntos[1].x" v-bind:cy="objcontenido.puntos[1].y" r="10" stroke="black" stroke-width="3" fill="black" />
         </svg>
         <canvas ref="canvastriangulo" v-if="this.objcontenido.puntos[1].figop=='triangulo'"  v-bind:id="this.objcontenido.puntos[1].figop" class="cva" width="250px" height="200px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas>
       </div>
       
       <div class="opcion1">
         <svg  width="250px" height="200px" class="figura1">
           <path  v-bind:id="cargar_fig_geometrica.tipofigura" style="stroke: #858F98;stroke-width:5; fill: #EFF3FB; stroke-dasharray:12 12;" d="m43,100 a85,85 0 1, 0 0,-1 z"></path>
           <image v-if="cargar_fig_geometrica.puntos[2].img=='poligonos'" style="display:none;" id="izC" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[2].x-30" v-bind:y="objcontenido.puntos[2].y-4"/>
           <circle display="none" id="pinicioC" v-bind:cx="objcontenido.puntos[2].x" v-bind:cy="objcontenido.puntos[2].y" r="10" stroke="black" stroke-width="3" fill="black" />
         </svg>
         <canvas ref="canvascirculo" v-if="this.objcontenido.puntos[2].figop=='circulo'" v-on:click="validar_post_trazo('circulo')"   v-bind:id="this.objcontenido.puntos[2].figop" class="cva" width="250px" height="200px" v-hammer:panstart="captureOn" v-hammer:pan="mo" v-hammer:panend="captureOff"></canvas>
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
      canvasB:null,
      canvasC:null,
      context:null,
      contextB:null,
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
      ordenvisitado:[],
      mostrar_pasos_T:null,
      paso_mostrar:0
      
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
        // var random_llena= Math.ceil(Math.random()*3);
        var random_llena= 1; 
        if(random_llena==1){  
            this.objcontenido={
            tipofigura:"cuadrado",
            direccion:"pandown",
            inicio:[{x:36,y:16}],
            final:[{x:36,y:16}],
            pociciones:[{xp:36,yp:184,L:"1"},
                        {xp:209,yp:184,L:"2"},
                        {xp:209,yp:16,L:"3"},
                        {xp:60,yp:16,L:"4"}],
            puntos:[{figop:"cuadrado",direccion:"pandown",x:36,y:16,img:"rectan"},{figop:"triangulo",direccion:"panright",x:138,y:20,img:"poligonos"},{figop:"circulo",direccion:"panleft",x:127,y:12,img:"poligonos"}]
          }
        }
        if(random_llena==2){  
            this.objcontenido={
            tipofigura:"triangulo",
            direccion:"panright",
            inicio:[{x:138,y:20}],
            final:[{x:138,y:20}],
            pociciones:[{xp:35,yp:168,L:"1"},
                        {xp:221,yp:168,L:"2"},
                        {xp:150,yp:40,L:"3"}],
            puntos:[{figop:"cuadrado",direccion:"pandown",x:36,y:16,img:"rectan"},{figop:"triangulo",direccion:"panright",x:138,y:20,img:"poligonos"},{figop:"circulo",direccion:"panleft",x:127,y:12,img:"poligonos"}]
          }
        }
        if(random_llena==3){  
            this.objcontenido={
            tipofigura:"circulo",
            inicio:[{x:127,y:11}],
            final:[{x:127,y:11}],
            direccion:"panright",
            pociciones:[{xp:130,yp:185,L:"1"},
                        {xp:163,yp:24,L:"2"}],
            puntos:[{figop:"cuadrado",direccion:"pandown",x:36,y:16,img:"rectan"},{figop:"triangulo",direccion:"panright",x:138,y:20,img:"poligonos"},{figop:"circulo",direccion:"panleft",x:127,y:12,img:"poligonos"}]
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
          //  this.limpiar_trazo(valor)
           this.responder(valor);
         },500);
       }
       return this.click_figura_correcta
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
     validar_post_trazo(valor_cli){
       if(valor_cli=="circulo"){
         console.log("hola")
       }
      //  if(valor_cv=="triangulo"){}
      //  if(valor_cv=="cuadrado"){}
     },
     limpiar_trazo(value){
       console.log(value)
       var canvas=null;
       var canvasB=null;
       var canvasC=null;
       var ctx=null;
      if(value=="cuadrado"){

         canvas =this.$refs.canvascuadrado  
         ctx=canvas.getContext("2d");
         ctx.clearRect(0, 0, canvas.width, canvas.height);
       }
      if(value=="circulo"){

         canvasC = this.$refs.canvascirculo  
         ctx=canvasC.getContext("2d");
         ctx.clearRect(0, 0, canvasC.width, canvasC.height); 
       }
      if(value=="triangulo"){

          canvasB =this.$refs.canvastriangulo 
          ctx=canvasB.getContext("2d");
          ctx.clearRect(0, 0, canvasB.width, canvasB.height);
          
       }
   
        
      // this.startX=this.caminoX;
      //   this.startY=this.caminoY;
     },
     cargar_figura(){
        this.llenado_bar=0
      this.milisegundos=0
      this.segundos=0
      //  console.log(this.objcontenido);
        setTimeout(() => {
            document.getElementById('pantalla1').style.display='none'; 
            this.$emit("tiemporespuestas",true); 
            this.mostrar=this.mostrarvista2;
            //  this.iniciando();
            document.getElementById('pantalla2').style.display='block'; 
            document.getElementById('pinicio').style.display='block';
            document.getElementById('pinicioB').style.display='block';
            document.getElementById('pinicioC').style.display='block';
           document.getElementById('iz').style.display='block';
            document.getElementById('izB').style.display='block';
             document.getElementById('izC').style.display='block';
            // this.$emit("mostrartime",true);
         },5000);  
     },
    responder(valorcva){
       this.$emit("tiemporespuestas",false); 
      //  this.parar_tiempo();

       this.llave_finalizar=true;

       if(this.calificando==false){
         var aciertos=0;
         var orden=false;
        
         for (let j = 0; j < this.objcontenido.pociciones.length; j++) {
           if(this.ordenvisitado.includes(this.objcontenido.pociciones[j].L)){
             aciertos+=1;
           }
         }
         if(this.ordenvisitado.length==this.objcontenido.pociciones.length){
          for (let v = 0; v < this.ordenvisitado.length; v++) {
           if(this.ordenvisitado[v]==this.objcontenido.pociciones[v].L){
             orden=true;
           }
          }
         }
         var aciertostotales= aciertos== this.objcontenido.pociciones.length?true:false;
         var patroninicial = this.objcontenido.pociciones[0].L== this.ordenvisitado[0]?true:false;
         var patronfinal = this.objcontenido.pociciones[this.objcontenido.pociciones.length-1].L== this.ordenvisitado[this.ordenvisitado.length-1]?true:false;
        
        //  this.parar_tiempo();
         if(this.click_figura_correcta==true & this.inicie_enelpunto==true & aciertostotales==true & patroninicial==true & patronfinal==true & orden==true){
           this.$emit("respuestasalumno",true);
         }else{
           console.log(valorcva)
           this.limpiar_trazo(valorcva)
           document.getElementById("pantallaActividad").style.backgroundColor='#F6535DCC';
           this.mostra_pasos()
           
          //  document.getElementById('indicador').style.display='block';                   
          //  this.automatico()
          //  this.$emit("respuestasalumno",false); 
         }
         
       }
       this.calificando=true
     },
    trazar(clientX,clientY,estoyen){ 
       
       var rect;
     
      if(estoyen=="cuadrado"){
         startX=this.startXC
         startY=this.startYC
         this.canvas =this.$refs.canvascuadrado  
         this.context=this.canvas.getContext("2d");
         rect= this.canvas.getBoundingClientRect();
       }
      if(estoyen=="circulo"){
         startX=this.startXR
         startY=this.startYR
         this.canvasC =this.$refs.canvascirculo  
         this.context=this.canvasC.getContext("2d");
         rect= this.canvasC.getBoundingClientRect();
        
       }
      if(estoyen=="triangulo"){
         startX=this.startXT
         startY=this.startYT
          this.canvasB =this.$refs.canvastriangulo 
          this.context=this.canvasB.getContext("2d");
          rect= this.canvasB.getBoundingClientRect();
       }
       var x=clientX-rect.left;
       var y=clientY-rect.top;
       var startX;
       var startY;
      // console.log(parseInt(x),parseInt(y))
      if(this.llave_punto_inicial==false){
        console.log(parseInt(x),parseInt(y),"entrepero")
        setTimeout(() => {
          this.mi_ini_llave1=true
         },3000);
        if(x<(this.objcontenido.inicio[0].x+30) & y<(this.objcontenido.inicio[0].y+20))
        {
         this.inicie_enelpunto=true
         this.llave_punto_inicial=true
         console.log("iniciaste bien")
        var xcir= 0
        var ycir= 0
        var L=""
        this.context.strokeStyle = "red";
        this.context.fillStyle = "#6ab150";
        for (let k = 0; k < this.objcontenido.pociciones.length; k++) {
          
          xcir=this.objcontenido.pociciones[k].xp;
          ycir=this.objcontenido.pociciones[k].yp;
          this.context.beginPath();
          
          this.context.arc(xcir, ycir, 10, 0, 9 * Math.PI);
          //  this.context.stroke();
        }
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
           this.responder(estoyen) 
          }
          
        }
        for (var k = 0; k < this.objcontenido.pociciones.length; k++) {
          xcir=this.objcontenido.pociciones[k].xp;
          ycir=this.objcontenido.pociciones[k].yp;
          L= this.objcontenido.pociciones[k].L;  
          this.marcarPos(xcir,x,ycir,y,L)
        }

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
    marcarPos( px,x,py,y,indice) {
      
      if(x<px+20 & px-20<x & y<py+20 & py-20<y){
         
         if(this.ordenvisitado[this.ordenvisitado.length-1]!=indice){
           this.ordenvisitado.push(indice)
           console.log(indice)
         }
         
      }
       
     
    },
     mo: function(e) {

      if (this.captureToggle==true & this.llave_finalizar==false) {
      var dondeestoy= e.target.id  
      var x= e.center.x;
      var y= e.center.y;
      var figura_clikeada= this.llave_figura_correcta==false?this.figura_correcta(dondeestoy):true;
      
      if(figura_clikeada){
      if(this.llave_direccion===false & this.evaluacion_unica===false){
        // console.log("estoy en direccion")
      //  if(e.additionalEvent=="panleft" | e.additionalEvent=="panright"){
      //    this.direccion(e.additionalEvent,dondeestoy)
      //   console.log(this.llave_direccion)
      //  }
      }
      this.trazar(x,y,dondeestoy)
      }
      // else{
      //   console.log(dondeestoy,x,y)
      // }
     }
    },
     captureOn: function() {
        // if(this.llave){
      // console.log(this.captureToggle)  
      this.captureToggle = true
      this.isDrawing=true
      //  }
    },
     captureOff: function() {
      this.captureToggle = false
      // console.log(this.captureToggle)
       this.isDrawing=false;
    },
    mostra_pasos(){
       this.mostrar_pasos_T = setInterval(
       this.rutacorrecta,1500);
    },
     rutacorrecta(){
       
       if(this.objcontenido.tipofigura=="cuadrado"){

         this.canvas =this.$refs.canvascuadrado  
         this.context=this.canvas.getContext("2d");
       }
      if(this.objcontenido.tipofigura=="circulo"){
         this.canvasC = this.$refs.canvascirculo  
         this.context=this.canvasC.getContext("2d");
       }
       if(this.objcontenido.tipofigura=="triangulo"){
          this.canvasB =this.$refs.canvastriangulo 
          this.context=this.canvasB.getContext("2d");     
       }
      if(this.objcontenido.tipofigura=="triangulo" | this.objcontenido.tipofigura=="cuadrado"){     
      if(this.paso_mostrar<this.objcontenido.pociciones.length-1){ 
        this.context.beginPath();
        this.context.lineWidth=3;
        this.context.strokeStyle ="#01E19E";
        this.context.fillStyle = "#6ab150";
        this.context.arc(this.objcontenido.pociciones[this.paso_mostrar].xp,
        this.objcontenido.pociciones[this.paso_mostrar].yp, 8, 0, 9 * Math.PI);
        this.context.font = "25px Courier New";  
        this.context.strokeText(this.objcontenido.pociciones[this.paso_mostrar].L, this.objcontenido.pociciones[this.paso_mostrar].xp-6, this.objcontenido.pociciones[this.paso_mostrar].yp+5);
        this.context.fill();
        this.context.stroke();
        if(this.paso_mostrar==0){
        this.context.beginPath();
        this.context.lineWidth=8;
        this.context.strokeStyle = "#01E19E";
        this.context.moveTo(this.objcontenido.inicio[0].x, this.objcontenido.inicio[0].y);
				this.context.lineTo(this.objcontenido.pociciones[0].xp,this.objcontenido.pociciones[0].yp);
        this.context.stroke();
        }if(this.paso_mostrar>=1){
        this.context.beginPath();
        this.context.lineWidth=8;
        this.context.strokeStyle = "#01E19E";
        this.context.moveTo(this.objcontenido.pociciones[this.paso_mostrar-1].xp, this.objcontenido.pociciones[this.paso_mostrar-1].yp);
				this.context.lineTo(this.objcontenido.pociciones[this.paso_mostrar].xp,this.objcontenido.pociciones[this.paso_mostrar].yp);
        this.context.stroke();
        }
      }
      else{
        this.context.beginPath();
        this.context.lineWidth=3;
        this.context.strokeStyle ="#01E19E";
        this.context.fillStyle = "#6ab150";
        this.context.arc(this.objcontenido.inicio[0].x,
        this.objcontenido.inicio[0].y, 8, 0, 9 * Math.PI);
        this.context.fill();
        this.context.stroke();
        this.context.beginPath();
        this.context.lineWidth=8;
        this.context.strokeStyle = "#01E19E";
        this.context.moveTo(this.objcontenido.pociciones[this.paso_mostrar-1].xp, this.objcontenido.pociciones[this.paso_mostrar-1].yp);
				this.context.lineTo(this.objcontenido.final[0].x,this.objcontenido.final[0].y);
        this.context.stroke();
        clearInterval(this.mostrar_pasos_T)
        this.$emit("respuestasalumno",false); 
      }
       }
       if(this.objcontenido.tipofigura=="circulo"){
         if(this.paso_mostrar==0){
        let x = 130, y = 100,radio = 85;
        this.context.beginPath();
        this.context.lineWidth=8;
        this.context.strokeStyle = "#01E19E";
        this.context.arc(x, y, radio, 1.5, 4.7);
        this.context.stroke();
        this.context.beginPath();
        this.context.lineWidth=3;
        this.context.strokeStyle ="#01E19E";
        this.context.fillStyle = "#6ab150";
        this.context.arc(this.objcontenido.pociciones[this.paso_mostrar].xp,
        this.objcontenido.pociciones[this.paso_mostrar].yp, 8, 0, 9 * Math.PI);
        this.context.fill();
        this.context.stroke();

         }if(this.paso_mostrar==1){
        var canvasC=null;
        canvasC = this.$refs.canvascirculo  
        this.context=canvasC.getContext("2d");
        this.context.clearRect(0, 0, canvasC.width, canvasC.height); 
        
        let xb = 130, yb = 100,radiob = 85;
        this.context.beginPath();
        this.context.lineWidth=8;
        this.context.strokeStyle = "#01E19E";
        this.context.arc(xb,yb, radiob, 0, 9);
        this.context.stroke();
        this.context.beginPath();
        this.context.lineWidth=3;
        this.context.strokeStyle ="#01E19E";
        this.context.fillStyle = "#6ab150";
        this.context.arc(this.objcontenido.pociciones[this.paso_mostrar-1].xp,
        this.objcontenido.pociciones[this.paso_mostrar-1].yp, 8, 0, 9 * Math.PI);
        this.context.fill();
        this.context.stroke();
        this.context.beginPath();
        this.context.lineWidth=3;
        this.context.strokeStyle ="#01E19E";
        this.context.fillStyle = "#6ab150";
        this.context.arc(this.objcontenido.inicio[0].x,
        this.objcontenido.inicio[0].y, 8, 0, 9 * Math.PI);
        this.context.fill();
        this.context.stroke();
        
        clearInterval(this.mostrar_pasos_T)
        this.$emit("respuestasalumno",false); 
         
         }
         
       }
      console.log(this.paso_mostrar);
      this.paso_mostrar+=1;
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
  display: none;
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
