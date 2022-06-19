<template>
<body>

  <div id="app"> 
    <Header :colorMostrar="color"/>

    <Navigator @isHard="dificultad=$event" @reseteo="reset=$event" @cantidad="cantidad=$event"
     @actualiza="act=$event" :msj="mens()" />
     
    <Container :esDificil="dificultad" :cant="cantidad" @colorEncontrar="color=$event"
     @arrayColores="array=$event" :actualizar="act" @ganador="gano=$event"/>

  </div>
  
  </body>
</template>

<script>
import Navigator from './components/Navigator.vue'
import Container from './components/Container.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
    Container,
    Navigator,
  },
  
  data () {
      return {
        dificultad:true,
        color:'',
        array:[],
        cantidad:6,
        act:0,
        gano:[false,1],
        mensaje:''
      }
  },
  methods: {
    colorBusc(){
        const arr = this.array
        return this.color=arr[1]

    },

    mens(){
      let msj=''
      if(this.gano[1]==2){
        msj='You Picked Right!'
      }
      else if(this.gano[1]==1){
        msj='Try Again!'
      }
      return msj
    }
   },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
	background: #232323;
	margin: 0;
	font-family: "Montserrat", "Avenir";
}
</style>
