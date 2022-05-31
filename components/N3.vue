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
      <svg  v-if="cargar_fig_geometrica.tipofigura=='estrella'" width="442" height="417" viewBox="0 0 442 417" fill="none" class="figura1">
        <path v-if="cargar_fig_geometrica.tipofigura=='estrella'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M220.043 0L154.987 139.959L0 158.172L114.805 265.538L88.974 417L220.043 345.103L360.68 417L332.935 265.538L442 158.172L289.883 139.959L220.043 0Z" fill="#FFCC0D"/>
        <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 

      </svg>
      <!-- trazos 2 -->
      <svg v-if="cargar_fig_geometrica.tipofigura=='cuadrado'" width="450" height="410" viewBox="-20 -20 435 410" fill="none" class="figura1">
       <rect v-if="cargar_fig_geometrica.tipofigura=='cuadrado'" v-bind:id="cargar_fig_geometrica.tipofigura" width="400" height="385" fill="#FFCC0D"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" /> 

      </svg>
      <svg  v-if="cargar_fig_geometrica.tipofigura=='triangulo'" width="483" height="405" viewBox="0 0 483 405" fill="none" class="figura1">
      <path v-if="cargar_fig_geometrica.tipofigura=='triangulo'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M0 380L249.191 0L483 380H0Z" fill="#FF96C9"/>
       <image v-if="cargar_fig_geometrica.puntos[0].img=='circunferenciainv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthc.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" />       
      </svg>
      <svg v-if="cargar_fig_geometrica.tipofigura=='rombo'"  width="450" height="419" viewBox="0 0 450 419" fill="none" class="figura1">
        <path v-if="cargar_fig_geometrica.tipofigura=='rombo'" v-bind:id="cargar_fig_geometrica.tipofigura" d="M219.46 0L0 211.066L219.46 419L450 211.066L219.46 0Z" fill="#87A3FA"/>
        <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" />
      </svg>
      <svg v-if="cargar_fig_geometrica.tipofigura=='trapecio'" width="601" height="406" viewBox="-20 -20 601 406" fill="none" class="figura1">
      <polygon v-if="cargar_fig_geometrica.tipofigura=='trapecio'" v-bind:id="cargar_fig_geometrica.tipofigura" points="150,25 460,25 570,350 50,350" fill="#00987E"/>
        <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectan'" style="display:none;" id="circunferencia" xlink:href="@/assets/down.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='rectaninv'" style="display:none;" id="circunferencia" xlink:href="@/assets/rigthin.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+25" v-bind:y="objcontenido.puntos[0].y-18"/>
         <circle style="display:none;" id="pinicio" v-bind:cx="objcontenido.puntos[0].x" v-bind:cy="objcontenido.puntos[0].y" r="10" stroke="black" stroke-width="3" fill="black" />
      </svg>
      <svg v-if="cargar_fig_geometrica.tipofigura=='rectangulo'" width="750" height="320" viewBox="-30 -20 856 290" fill="none" class="figura1">
        <rect v-if="cargar_fig_geometrica.tipofigura=='rectangulo'" v-bind:id="cargar_fig_geometrica.tipofigura" width="740" height="275" fill="#0832B5"/>
       <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonos'" style="display:none;" id="circunferencia" xlink:href="@/assets/downi.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x-30" v-bind:y="objcontenido.puntos[0].y-20"/>
         <image v-if="cargar_fig_geometrica.puntos[0].img=='poligonosinv'" style="display:none;" id="circunferencia" xlink:href="@/assets/downpol.png"  width="20" height="20" v-bind:x="objcontenido.puntos[0].x+15" v-bind:y="objcontenido.puntos[0].y-18"/>
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
    eleccion_plantilla: String
  },
   data: function(){
    return{
      ctx:null,
      inmax:0,
      rect:null,
      mostrar:true,
      myElement:"",
      canvas:null,
      context:null,
      isDrawing:false,
      mostrar_pasos_T:null,
      paso_mostrar:0,
      
      
      
      llavedesvio:false,
      margen_limite:20,
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
    this.ctx=this.canvas.getContext("2d");
 
     this.cargar_figura();
   },
   methods:{
  
     obtenercontenido(){
       var random_llena= Math.ceil(Math.random()*5);
        // var random_llena= 5; 
        console.log(this.eleccion_plantilla)
        if(this.eleccion_plantilla=="preTrazosFormaFigura2"){

        if(random_llena==1){  
            this.objcontenido={
            tipofigura:"cuadrado",
            direccion:"pandown",//esta es la direccion correcta
            inicio:[{x:207,y:25}],
            final:[{x:207,y:25}],
            pociciones:[{xp:202,yp:402,L:"1"},
                        {xp:600,yp:402,L:"2"},
                        {xp:600,yp:25,L:"3"},
                        {xp:246,yp:25,L:"4"}],
            puntos:[{figop:"cuadrado",direccion:"pandown",x:5,y:10,img:"rectan"}],
          }
        }
        if(random_llena==2){  
            this.objcontenido={
            tipofigura:"triangulo",
            direccion:"panright",
            inicio:[{x:407,y:6}],
            final:[{x:407,y:6}],
             pociciones:[{xp:646,yp:378,L:"1"},
                        {xp:159,yp:378,L:"2"},
                        {xp:381,yp:40,L:"3"}],
            puntos:[{figop:"circulo",direccion:"panright",x:250,y:15,img:"poligonosinv"}],
          }
        }
        if(random_llena==3){  
            this.objcontenido={
            tipofigura:"rombo",
            inicio:[{x:394,y:8}],
            final:[{x:394,y:8}],
            direccion:"panright",
            pociciones:[{xp:178,yp:209,L:"1"},
                        {xp:395,yp:416,L:"2"},
                        {xp:624,yp:209,L:"3"},
                        {xp:428,yp:32,L:"4"}],
            puntos:[{figop:"rombo",direccion:"panright",x:220,y:15,img:"poligonos"}],
          }
        }
        if(random_llena==4){  
            this.objcontenido={
            tipofigura:"trapecio",
            inicio:[{x:269,y:42}],
            final:[{x:269,y:42}],
            direccion:"panright",
            pociciones:[{xp:578,yp:46,L:"1"},
                        {xp:691,yp:372,L:"2"},
                        {xp:169,yp:372,L:"3"},
                        {xp:257,yp:77,L:"4"}],
            puntos:[{figop:"Trapecio",direccion:"panright",x:150,y:25,img:"rectaninv"}],
          }
        }
        if(random_llena==5){  
            this.objcontenido={
            tipofigura:"rectangulo",
            inicio:[{x:52,y:50}],
            final:[{x:52,y:50}],
            direccion:"panright",
             pociciones:[{xp:697,yp:54,L:"1"},
                        {xp:697,yp:290,L:"2"},
                        {xp:52,yp:290,L:"3"},
                        {xp:52,yp:88,L:"4"}],
            puntos:[{figop:"Rectangulo",direccion:"panright",x:5,y:5,img:"rectaninv"}],
          }
        }

        }
        if(this.eleccion_plantilla=="preTrazosFormaFigura3"){
          
        if(random_llena==1){  
            this.objcontenido={
            tipofigura:"flecha",
            direccion:"pandown",//esta es la direccion correcta
            inicio:[{x:390,y:20}],
            final:[{x:390,y:20}],
            pociciones:[{xp:389,yp:108,L:"1"},
                        {xp:101,yp:110,L:"2"},
                        {xp:101,yp:239,L:"3"},
                        {xp:389,yp:239,L:"4"},
                        {xp:389,yp:335,L:"5"},
                        {xp:661,yp:176,L:"6"},
                        {xp:419,yp:28,L:"7"}],
            puntos:[{figop:"flecha",direccion:"pandown",x:338,y:15,img:"rectan"}],
  
          }
        }
        if(random_llena==2){  
            this.objcontenido={
            tipofigura:"cruz",
            direccion:"panright",
            inicio:[{x:471,y:127}],
            final:[{x:471,y:127}],
             pociciones:[{xp:602,yp:128,L:"1"},
                        {xp:602,yp:274,L:"2"},
                        {xp:467,yp:276,L:"3"},
                        {xp:465,yp:395,L:"4"},
                        {xp:332,yp:397,L:"5"},
                        {xp:328,yp:278,L:"6"},
                        {xp:200,yp:277,L:"7"},
                        {xp:196,yp:134,L:"8"},
                        {xp:326,yp:134,L:"9"},
                        {xp:326,yp:5,L:"10"},
                        {xp:467,yp:5,L:"11"},
                        {xp:464,yp:91,L:"12"}],
            puntos:[{figop:"cruz",direccion:"panright",x:270,y:127,img:"rectaninv"}],
          }
        }
        if(random_llena==3){  
            this.objcontenido={
            tipofigura:"irregular",
            inicio:[{x:397,y:222}],
            final:[{x:397,y:222}],
            direccion:"panright",
            pociciones:[{xp:632,yp:357,L:"1"},
                        {xp:299,yp:421,L:"2"},
                        {xp:166,yp:185,L:"3"},
                        {xp:374,yp:2,L:"4"},
                        {xp:390,yp:183,L:"5"}],
            puntos:[{figop:"irregular",direccion:"panright",x:230,y:222,img:"poligonosinv"}],
          }
        }
        if(random_llena==4){  
            this.objcontenido={
            tipofigura:"octagono",//figura que mostara
            inicio:[{x:550,y:80}],//donde debe iniciar
            final:[{x:550,y:80}],// donde debe finalizar
            direccion:"pandown",//direccion correcta
            pociciones:[{xp:587,yp:233,L:"1"},
                        {xp:480,yp:366,L:"2"},
                        {xp:316,yp:371,L:"3"},
                        {xp:204,yp:236,L:"4"},
                        {xp:245,yp:78,L:"5"},
                        {xp:393,yp:1,L:"6"},
                        {xp:515,yp:51,L:"7"}],//vertices de la figura
             puntos:[{figop:"octagono",direccion:"pandown",
                        x:390,y:85,img:"poligonosinv"}],//svg inicia a dib,dir
          }
        }
        if(random_llena==5){  
            this.objcontenido={
            tipofigura:"estrella",
            inicio:[{x:510,y:259}],
            final:[{x:510,y:259}],
            direccion:"panright",
            pociciones:[{xp:538,yp:413,L:"1"},
                        {xp:396,yp:338,L:"2"},
                        {xp:270,yp:412,L:"3"},
                        {xp:290,yp:270,L:"4"},
                        {xp:178,yp:158,L:"5"},
                        {xp:330,yp:140,L:"6"},
                        {xp:395,yp:5,L:"7"},
                        {xp:467,yp:135,L:"8"},
                        {xp:616,yp:157,L:"9"},
                        {xp:541,yp:234,L:"10"}],//vertices de la figura
            puntos:[{figop:"estrella",direccion:"panright",x:330,y:260,img:"poligonosinv"}],
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
         },20000);  
     },
     responder(){
       
      this.$emit("tiemporespuestas",false); 
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
        
        console.log("ac:"+aciertostotales,"pati:"+patroninicial,"patf:"+patronfinal,"cadena:"+this.ordenvisitado)
        console.log(this.objcontenido.pociciones[this.objcontenido.pociciones.length-1].L,"=",this.ordenvisitado[this.ordenvisitado.length-1])
         if(this.click_figura_correcta==true & this.inicie_enelpunto==true & aciertostotales==true & patroninicial==true & patronfinal==true & orden==true){
           
           this.$emit("respuestasalumno",true);
         }else{
           this.limpiar_trazo();
            this.mostra_pasos();
            document.getElementById("pantallaActividad").style.backgroundColor='#F6535DCC'

           
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


      // console.log(parseInt(startX),parseInt(startY))
      if(this.llave_punto_inicial==false){
        
        setTimeout(() => {
          this.mi_ini_llave1=true
         },2000);

        if(x<(this.objcontenido.inicio[0].x+20) & y<(this.objcontenido.inicio[0].y+20))
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
          
          this.context.arc(xcir, ycir, 20, 0, 9 * Math.PI);
          // this.context.stroke();
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
        //  this.texts(x,y)
      if(x>=this.objcontenido.final[0].x-10 & x<=this.objcontenido.final[0].x+10 & y>=this.objcontenido.final[0].y-10 & y<=this.objcontenido.final[0].y){
          if(this.mi_ini_llave1==true){
           this.responder();      
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
    mostra_pasos(){
       this.mostrar_pasos_T = setInterval(
       this.rutacorrecta,1500);
    },
     rutacorrecta(){
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
        this.context.arc(this.objcontenido.final[0].x,
        this.objcontenido.final[0].y, 8, 0, 9 * Math.PI);
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
      console.log(this.paso_mostrar);
      this.paso_mostrar+=1;
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
      
      if(figura_clikeada==true & this.llavedesvio==false){
      //  console.log(dondeestoy)
      // if(this.llave_direccion===false & this.evaluacion_unica===false){
   
      //    this.direccion(e.additionalEvent,dondeestoy)
      
      // }
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
  // outline: solid 2px red;
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
  margin-top: 10px;
      display: flex;
    justify-content: center;
    height: 450px;
    width: 830px;
}


</style>
