<template>
  <section class="src-components-header">
    <div id="header" :style="{'background-color': colorGanador}">
      <h1>
      The Great
      <br />
      <span id="colorDisplay">{{pickedColor}} </span>
      <br />Guessing Game
      </h1>
    </div>
  </section>
</template>

<script>

  export default  {
    name: 'src-components-header',
    props: ['pickedColor','colorGanador'],
    mounted () {
    this.style='background-color:steelblue '
    },
    data () {
      return {

      }
    },
    methods: {
    cambiarBackground(pickedColor){
    this.style='background-color: ' + pickedColor
    }
    },
    computed: {
    }
  }

</script>

<style scoped lang="css">

h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
#colorDisplay {
  font-size: 200%;
}
#header {
  transition: all 0.3s;
  background: steelblue;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}
h1 {
  display: block;
  font-size: 2em;
  margin-block-start: 0.67em;
  margin-block-end: 0.67em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
}
h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
</style>
