<template>

      <section class="src-components-square" :style="fondo(colorPicker)" @click="analizar(colorPicker)">
      </section>

</template>

<script>

  export default  {
    name: 'src-components-square',
    props: ['color','colorPicker','actualiza','array'],
    mounted () {
      this.colorAbuscar=this.colorPicker
    },
    data () {
      return {
        msj:'',
        colorAbuscar:'',
        gano:false
      }
    },
    methods: {
      analizar(color){
        this.ver=true
        if(this.color==color){
          this.msj='gano'
          this.gano=true
          this.fondo()
        }else{
          this.background='rgb(35, 35, 35)'//color fondo
          this.msj='perdio'
          
        }
        //this.$emit('mens',this.msj)
        return this.msj
      },
      fondo(colorP){
        let color=''
        let num=0
        if(this.msj==''){
          color=this.color
        }
        else if(this.msj=='perdio'){
          color='rgb(35, 35, 35)'
          num=1
          this.$emit('gano',[this.gano,num])
        }
        else{
          color=colorP
          num=2
          this.$emit('gano',[this.gano,num])
        }
        return {
          backgroundColor:color
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-square {
  width: 30%;
	background: blue;
	padding-bottom: 30%;
	float: left;
	margin: 1.66%;
	border-radius: 10%;
	transition: background 0.8s;
	-webkit-transition: background 0.8s;
	-moz-transition: background 0.8s;
  }
</style>
