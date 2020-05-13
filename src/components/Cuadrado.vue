<template>
  <section class="src-components-cuadrado">
    <div class="square" :style="style" @click="mostrarColor"></div>
  </section>
</template>

<script lang="js">

  export default  {
    name: 'src-components-cuadrado',
    props: ['color','destroyed','message','pickedColor'],
    mounted () {
    
    },
    destroyed() {
    console.log("Componente eliminado");
     this.$destroy();
    },
    data () {
      return {

      }
    },
    methods: {
    mostrarColor(){
      if (this.pickedColor!=this.color){
       this.color = "#232323" 
       this.$emit('verificar',this.color)
      }
      else {
      this.$emit('verificar',this.color)
      }
    }
     ,
    },
    computed: {
      style () {
        return 'background-color: ' + this.color;
      }
    },
}
</script>

<style scoped lang="css">
.square {
  width: 30%;
  /*  background: blue; */
  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
</style>
