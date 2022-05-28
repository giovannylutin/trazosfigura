<template>
  <div class="pretrazos3">
    <div id="pantalla1" class="pretrazos3_figura">
     <div class="Rectangulo">
       <svg v-if="cargar_fig_geometrica.tipofigura=='flecha'" width="600px" height="400px" viewBox="0 0 700 450" fill="none" class="figura1">
        <path v-if="cargar_fig_geometrica.tipofigura=='flecha'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M338.649 0V119.665H0V274.117H338.649V391L655 194.804L338.649 0Z" fill="#FF8001"/>
        
         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferencia'" style="display:none;" id="circunferencia" xlink:href="@/assets/leftc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
        
        <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 
       </svg>
       <svg v-if="cargar_fig_geometrica.tipofigura=='cruz'" width="600" height="400" viewBox="0 0 412 407" fill="none" class="figura1">
        <path v-if="cargar_fig_geometrica.tipofigura=='cruz'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M274.203 0H133.622V133.352H0V280.594H133.622V407H274.203V280.594H412V133.352H274.203V0Z" fill="#00987E"/>
        <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferencia'" style="display:none;" id="circunferencia" xlink:href="@/assets/leftc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 
         
      </svg>
      <svg v-if="cargar_fig_geometrica.tipofigura=='irregular'" width="469" height="422" viewBox="0 0 469 422" fill="none" class="figura1">
        <path v-if="cargar_fig_geometrica.tipofigura=='irregular'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M212.944 0L0 184.217L130.641 422L469 357.981L227.315 226.025L212.944 0Z" fill="#804DD7"/>
        <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 
         
      </svg>
      <svg v-if="cargar_fig_geometrica.tipofigura=='octagono'" width="429" height="414" viewBox="0 0 440 465" fill="none" class="figura1">
        <path v-if="cargar_fig_geometrica.tipofigura=='octagono'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M213.336 0L45.7703 82.9551L0 265.146L121.796 414H311.859L429 265.146L387.884 82.9551L213.336 0Z" fill="#87A3FA"/>
        <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 

      </svg>

         <!-- <svg width="500px" height="450px" class="figura1">
         <path v-if="cargar_fig_geometrica.tipofigura=='flecha'" v-bind:id="cargar_fig_geometrica.tipofigura"  d="M338.649 0V119.665H0V274.117H338.649V391L655 194.804L338.649 0Z" fill="#FF8001"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='cruz'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M274.203 0H133.622V133.352H0V280.594H133.622V407H274.203V280.594H412V133.352H274.203V0Z" fill="#00987E"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='irregular'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M212.944 0L0 184.217L130.641 422L469 357.981L227.315 226.025L212.944 0Z" fill="#804DD7"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='octagono'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M213.336 0L45.7703 82.9551L0 265.146L121.796 414H311.859L429 265.146L387.884 82.9551L213.336 0Z" fill="#87A3FA"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='estrella'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M220.043 0L154.987 139.959L0 158.172L114.805 265.538L88.974 417L220.043 345.103L360.68 417L332.935 265.538L442 158.172L289.883 139.959L220.043 0Z" fill="#FFCC0D"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='poligonoiregularA'" v-bind:id="cargar_fig_geometrica.tipofigura"  d="M0 0L401.538 73.8146L474 388L116.593 315.132L0 0Z" fill="#FF96C9"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='hexagono'" v-bind:id="cargar_fig_geometrica.tipofigura" xmlns="http://www.w3.org/2000/svg" d="M299.519 0H127.257L0 122.501V296.948L127.257 421H306.503L426 296.948V122.501L299.519 0Z" fill="#FFCC0D"/>
         <path v-if="cargar_fig_geometrica.tipofigura=='pentagono'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M219.818 0L0 159.086L86.357 419H361.129L443 159.086L219.818 0Z" fill="#0832B5"/>

         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferencia'" style="display:none;" id="circunferencia" xlink:href="@/assets/leftc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 
         
         </svg> -->
        
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
      ctx:null,
      rect:null,
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
      ordenvisitado:[]
      
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
    this.canvas =this.$refs.canvas  
    this.context=this.canvas.getContext("2d");
    
     this.cargar_figura();
   },
   methods:{
  
     obtenercontenido(){
        
        var random_llena= Math.ceil(Math.random()*4);
          // var random_llena= 1; 
        if(random_llena==1){  
            this.objcontenido={
            tipofigura:"flecha",
            direccion:"pandown",//esta es la direccion correcta
            inicio:[{x:390,y:20}],
            final:[{x:390,y:20}],
            pociciones:[{xp:389,yp:108,L:"A"},
                        {xp:101,yp:110,L:"B"},
                        {xp:101,yp:239,L:"C"},
                        {xp:389,yp:239,L:"D"},
                        {xp:389,yp:335,L:"E"},
                        {xp:661,yp:176,L:"F"}],
            puntos:[{figop:"flecha",direccion:"pandown",x:338,y:15,img:"rectan"}],
  
          }
        }
        if(random_llena==2){  
            this.objcontenido={
            tipofigura:"cruz",
            direccion:"panright",
            inicio:[{x:471,y:127}],
            final:[{x:471,y:127}],
             pociciones:[{xp:602,yp:128,L:"A"},
                        {xp:602,yp:274,L:"B"},
                        {xp:467,yp:276,L:"C"},
                        {xp:465,yp:395,L:"D"},
                        {xp:332,yp:397,L:"E"},
                        {xp:328,yp:278,L:"F"},
                        {xp:200,yp:277,L:"G"},
                        {xp:196,yp:134,L:"H"},
                        {xp:326,yp:134,L:"I"},
                        {xp:326,yp:5,L:"J"},
                        {xp:467,yp:5,L:"k"}],
            puntos:[{figop:"cruz",direccion:"panright",x:270,y:127,img:"rectaninv"}],
          }
        }
        if(random_llena==3){  
            this.objcontenido={
            tipofigura:"irregular",
            inicio:[{x:397,y:222}],
            final:[{x:397,y:222}],
            direccion:"panright",
            pociciones:[{xp:632,yp:357,L:"A"},
                        {xp:299,yp:421,L:"B"},
                        {xp:166,yp:185,L:"C"},
                        {xp:374,yp:2,L:"D"}],
            puntos:[{figop:"irregular",direccion:"panright",x:230,y:222,img:"poligonosinv"}],
          }
        }
        if(random_llena==4){  
            this.objcontenido={
            tipofigura:"octagono",//figura que mostara
            inicio:[{x:550,y:80}],//donde debe iniciar
            final:[{x:550,y:80}],// donde debe finalizar
            direccion:"pandown",//direccion correcta
            pociciones:[{xp:587,yp:233,L:"A"},
                        {xp:480,yp:366,L:"B"},
                        {xp:316,yp:371,L:"C"},
                        {xp:204,yp:236,L:"D"},
                        {xp:245,yp:78,L:"E"},
                        {xp:393,yp:1,L:"F"}],//vertices de la figura
             puntos:[{figop:"octagono",direccion:"pandown",
                        x:390,y:85,img:"poligonosinv"}],//svg inicia a dib,dir
          }
        }
        if(random_llena==5){  
            this.objcontenido={
            tipofigura:"estrella",
            inicio:[{x:25,y:25}],
            final:[{x:25,y:25}],
            direccion:"panright",
            puntos:[{figop:"estrella",direccion:"panright",x:25,y:25,img:"poligonosinv"}],
          }
        }
        if(random_llena==6){  
            this.objcontenido={
            tipofigura:"poligonoiregularA",
            inicio:[{x:300,y:50}],
            final:[{x:300,y:50}],
            direccion:"panright",
            puntos:[{figop:"poligonoiregularA",direccion:"panright",x:300,y:50,img:"rectaninv"}],
          }
        }
        if(random_llena==7){  
            this.objcontenido={
            tipofigura:"hexagono",
            inicio:[{x:580,y:115}],
            final:[{x:580,y:115}],
            direccion:"panleft",
            puntos:[{figop:"hexagono",direccion:"panleft",x:423,y:110,img:"rectan"}],
          }
        }
        if(random_llena==8){  
            this.objcontenido={
            tipofigura:"pentagono",
            inicio:[{x:370,y:15}],
            final:[{x:370,y:15}],
            direccion:"panright",
            puntos:[{figop:"pentagono",direccion:"panright",x:219,y:15,img:"poligonosinv"}],
          }
        }
        for (let j = 0; j < this.objcontenido.inicio.length; j++) {
          this.startXC=this.objcontenido.inicio[j].x
          this.startYC=this.objcontenido.inicio[j].y
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
           if(figura==="irregular"){
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
          var xcir;
          var ycir;
          this.ctx = this.canvas.getContext("2d");
          this.ctx.beginPath();
          moveTo(this.objcontenido.pociciones[0].xp, this.objcontenido.pociciones[0].yp);
          for (let h = 0; h < this.objcontenido.pociciones.length; h++) {
          xcir=this.objcontenido.pociciones[h].xp;
          ycir=this.objcontenido.pociciones[h].yp;
          this.ctx.lineTo(xcir, ycir);
          }
          this.ctx.closePath();
          this.ctx.stroke();
         },5000);  
     },
     responder(){
       
this.$emit("tiemporespuestas",false); 
       this.llave_finalizar=true;
       
       if(this.calificando==false){
         var aciertos=0;
        
         for (let j = 0; j < this.objcontenido.pociciones.length; j++) {
           if(this.ordenvisitado.includes(this.objcontenido.pociciones[j].L)){
             aciertos+=1;
           }
         }
         var aciertostotales= aciertos== this.objcontenido.pociciones.length?true:false;
         var patroninicial = this.objcontenido.pociciones[0].L== this.ordenvisitado[0]?true:false;
         var patronfinal = this.objcontenido.pociciones[this.objcontenido.pociciones.length-1].L== this.ordenvisitado[this.ordenvisitado.length-1]?true:false;
        
        
        console.log("ac:"+aciertostotales,"pati:"+patroninicial,"patf:"+patronfinal)
        console.log(this.objcontenido.pociciones[this.objcontenido.pociciones.length-1].L,"=",this.ordenvisitado[this.ordenvisitado.length-1])
         if(this.click_figura_correcta==true & this.inicie_enelpunto==true & aciertostotales==true & patroninicial==true & patronfinal==true){
           
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
       
       this.rect = this.canvas.getBoundingClientRect();     
       var x=clientX-this.rect.left;
       var y=clientY-this.rect.top;
       var startX;
       var startY;  
         startX=this.startXC
         startY=this.startYC


      console.log(parseInt(startX),parseInt(startY))
      if(this.llave_punto_inicial==false){
        
        setTimeout(() => {
          this.mi_ini_llave1=true
         },3000);

        if(x<(this.objcontenido.inicio[0].x+20) & y<(this.objcontenido.inicio[0].y+20))
        {
         this.inicie_enelpunto=true
         this.llave_punto_inicial=true
         console.log("iniciaste bien")
      
        var xcir= 0
        var ycir= 0
        var L=""
        


        this.context.strokeStyle = "red";
        for (let k = 0; k < this.objcontenido.pociciones.length; k++) {
          
          xcir=this.objcontenido.pociciones[k].xp;
          ycir=this.objcontenido.pociciones[k].yp;
          this.context.beginPath();
          this.context.arc(xcir, ycir, 20, 0, 9 * Math.PI);
          this.context.stroke();
        }
        
			// this.context.rect(20, 20, 150, 100);
        
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
         this.texts(x,y)
      if(x>=this.objcontenido.final[0].x-10 & x<=this.objcontenido.final[0].x+10 & y>=this.objcontenido.final[0].y-10 & y<=this.objcontenido.final[0].y){
          if(this.mi_ini_llave1==true){
           this.responder()      
          }
        
        }
       
       
        for (var k = 0; k < this.objcontenido.pociciones.length; k++) {
          xcir=this.objcontenido.pociciones[k].xp;
          ycir=this.objcontenido.pociciones[k].yp;
          L= this.objcontenido.pociciones[k].L;  
          this.marcarPos(xcir,x,ycir,y,L)
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
 texts(x,y){
    if (this.ctx.isPointInPath(x,y)) {
      console.log("hola");
      }
 },
    marcarPos( px,x,py,y,indice) {
      
      if(x<px+20 & px-20<x & y<py+20 & py-20<y){
         console.log(indice)
         this.ordenvisitado.push(indice)
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
  outline: solid 2px red;
  position: absolute;
  margin: auto;
  
}
.cva{
  outline: 2px solid magenta;
  position: relative;
}
#manita{
  position: relative;
}

.Rectangulo {
  margin-top: 10px;
      display: flex;
    justify-content: center;
    height: 450px;
    width: 830px;
}


</style>
