<template>

  <section class="src-components-navigator">

		<button id="reset" @click="resetea()"> New colors</button>
		<span id="message">{{mens()}} </span>

		<button id="easy" :class="{'selected':!this.isHard}" @click="easyButton()">easy</button>
		<button id="hard" :class="{'selected':this.isHard}" @click="hardButton()">hard</button> 

  </section>

</template>

<script >

  export default  {
    name: 'src-components-navigator',
    props: ['reseteo','msj'],
    mounted () {

    },
    data () {
      return {
      isHard:true,
      colorCount: 6,
      colors:[],
      reset:0,
      mensaje:'',
      contador:0,
      gano:''
      } 
    },
    methods: {
      easyButton(){
        if (this.isHard) {
          this.isHard = false;
          this.colorCount = 3;
          this.$emit('isHard',this.isHard);
          this.$emit('cantidad',this.colorCount);
          this.contador++;
          this.$emit('actualiza',this.contador);
      }
    },
       hardButton(){
          if (!this.isHard) {
            this.isHard = true
            this.colorCount = 6
            this.$emit('isHard',this.isHard);
            this.$emit('cantidad',this.colorCount);
            this.contador++;
            this.$emit('actualiza',this.contador);            
       }
      },
      resetea(){
          location.reload();
      },
      mens(){
        return this.msj
      }
    },
    computed: {
    }
}
 
</script>

<style scoped lang="css">
  .src-components-navigator {
  background: #ffffff;
	height: 30px;
	text-align: center;
	margin: 0;
	margin-top: -30px;
  }


h1 {
	font-weight: normal;
	line-height: 1.1;
	padding: 20px 0;

}
button {
	border: none;
	background-color: white;
	font-family: "Montserrat", "Avenir";
	text-transform: uppercase;
	height: 100%;
	font-weight: 700;
	letter-spacing: 1px;
	color: steelblue;
	transition: all 0.3s;
	outline: none;
}
button:hover {
	color: white;
	background-color: steelblue;
}
.selected {
	background-color: steelblue;
	color: white;
}
#message {
	color: #0f0f0f;
	display: inline-block;
	width: 20%;
}

</style>
