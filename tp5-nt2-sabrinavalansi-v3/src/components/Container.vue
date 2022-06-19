<template>

  <section class="src-components-container">

    <Square v-show="gano[0]==false" v-for="(color,index) in colors" :color="colors[index]" :key="index" :colorPicker="pickedColor"
    :actualiza="refrescar(actualizar)" @mens="mensajeSquare=$event" :array="colors" @gano="gano=$event"/>
    
    <Square v-show="gano[0]==true" v-for="(color,index) in colors" :color="colorGanador(pickedColor)" :key="index" :colorPicker="pickedColor"
    :actualiza="refrescar(actualizar)" @mens="mensajeSquare=$event" :array="colors" @gano="gano=$event" />

  </section>

</template>

<script >
import Square from './Square.vue'

  export default  {
    name: 'src-components-container',
    props: ['cant','esDificil','colorEncontar','actualizar'],
    components:{
      Square
    },
    mounted () {
      this.genColor(this.esDificil,this.cant)
    },
    data () {
      return {
        colors:this.calcularCant(),
        original:[],
        pickedColor:'',
        dificultad:true,
        mensajeSquare:'',
        gano:[false,0]
      }
    },
    methods: {
      genColor(dif,cant){
      this.dificultad=dif
      this.colors=this.createNewColors(cant)
      this.original=this.colors
      this.pickedColor=this.colorPicker(this.indiceAleatorio(3)) 
      this.$emit('colorEncontrar',this.pickedColor);
      this.$emit('arrayColores',this.colors);
      },

     refrescar(num){
        if(num>0){
        let arr=[] 
        for (var i = 0; i < this.cant; i++) {
          arr[i]=this.original[i]
        }
        if(this.cant<4){
          this.dificultad=false
        }else{
          this.dificultad=true
        }
        this.colors=arr
        }
     },

     colorGanador(color){
      this.$emit('ganador',this.gano)
      return color
     },

      calcularCant(dif){
        if(dif==true){
          this.cantColores=6
        }
        else{
          this.cantColores=3
        }
        return this.cantColores
      },

      createNewColors(num){
        var arr = [];
          for (var i = 0; i < num; i++) {
            arr.push(this.createRandomStringColor());
          }
        
        return arr;
      },

      createRandomStringColor(){
        var newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
        return newColor;
      },

      randomInt(){
        return Math.floor(Math.random() * 256);
      },

      colorPicker(index){
        let color='';
        color=this.colors[index];
        return color
      },

      indiceAleatorio() {
      return Math.floor(Math.random() * (3 - 1)) + 1;
      },

      restaurar(){
        this.genColor(this.dificultad,3);
      }
     
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-container {
  margin: 20px auto;
	max-width: 600px;
  }
</style>
