<template>
  <section class="src-components-juego">
    <div id="container">
      <Header :pickedColor="pickedColor" :colorGanador="colorGanador" />
      <div class="navbar">
        <div id="navigator">
          <button id="reset" @click="inicializarColores()">{{msgIni}}</button>
          <span id="message" msg>{{msg}}</span>
          <button id="easy" @click="dificultadEasy()" :style="{'background-color': colorBtEa, 'color': colorLtEa}">easy</button>
          <button id="hard" class="selected" @click="dificultadHard()" :style="{'background-color': colorBtHd, 'color': colorLtHd}">hard</button>
        </div>
      </div>
      <div id="cuadrado">
        <Cuadrado
          :pickedColor="pickedColor"
          :color="colores[cuadrado]"
          v-for="cuadrado in cuadrados"
          :key="cuadrado"
          @verificar="verificarColor"
        />
      </div>
    </div>
  </section>
</template>

<script>
import Header from "./Header.vue";
import Cuadrado from "./Cuadrado.vue";

export default {
  name: "src-components-juego",
  props: [],
  components: {
    Header,
    Cuadrado
  },
  mounted() {},
  created() {
    this.createNewColors();
  },
  data() {
    return {
      cuadrados: 6,
      colores: [],
      isHard: true,
      msg: '',
      msgIni:'New colors!',
      color: "rgb(59, 186, 0)",
      colorPerdedor: "rgb(0, 0, 0)",
      pickedColor: String,
      colorGanador: String,
      message: "",
      msgCuadrado: String,
      estadoEasy: true,
      estadoHard: true,
      colorBtHd: "rgb(70,130,180)",
      colorLtHd:"rgb(251, 251, 251)",
      colorBtEa:"rgb(251,251,251)",
      colorLtEa: "rgb(70, 130, 180)"
    };
  },

  methods: {
    verificarColor(colour) {
      console.log("diste click");
      console.log(colour);
      if (colour == this.pickedColor) {
        console.log("adivinaste");
        this.msg='You Picked Right!'
        this.msgIni='PLAY AGAIN!'
        this.colorGanador = this.pickedColor;
        this.CambColoresCuadrados();
      } else {
        this.msg='Try Again!'
        console.log("perdiste, proba otro");
      
      }
    },
    enviarColor() {
      this.$emit("cambiarColor", this.pickedColor);
    },

    CambColoresCuadrados() {
      this.colores = [];
      for (var i = 0; i <= this.cuadrados; i++) {
        this.colores.push(this.pickedColor);
 
      }
    },

    dificultadEasy() {
      if (this.estadoEasy) {
        this.cuadrados = 3;
        this.createNewColors();
        this.colorGanador = "";
        this.estadoEasy = false;
        this.estadoHard = true;
        this.colorBtEa = "rgb(70, 130, 180)"
        this.colorLtEa = "rgb(251,251,251)"
        this.colorBtHd = "rgb(251,251,251)"
        this.colorLtHd = "rgb(70, 130, 180)"
      }
    },

    dificultadHard() {
      if (this.estadoHard) {
        this.cuadrados = 6;
        this.createNewColors();
        this.colorGanador = "";
        this.estadoHard = false;
        this.estadoEasy = true;
        this.colorBtHd = "rgb(70,130,180)"
        this.colorLtHd = "rgb(251, 251, 251)"
        this.colorBtEa = "rgb(251,251,251)"
        this.colorLtEa = "rgb(70, 130, 180)"
      }
    },

    resetColor() {
      this.resetGame();
    },

    resetGame(number) {
      console.log(number);
    },
    inicializarColores() {
      this.createNewColors();
      this.colorGanador = "";
      this.msg='',
      this.msgIni= 'New colors!'
    },
    createNewColors() {
      this.colores = [];
      for (var i = 0; i <= this.cuadrados; i++) {
        this.colores.push(this.createRandomStringColor());
      }
      this.pickRandomColor();
     
    },
    pickRandomColor() {
      this.pickedColor = this.colores[
        Math.floor(Math.random() * this.cuadrados)
      ];
    },
    createRandomStringColor() {
      var newColor =
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")";
      //	console.log(newColor);
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    }
  },
  computed: {}
};
</script>

<style scoped lang="css">
#body {
  background: #232323;
  margin: 0;
  font-family: "Montserrat", "Avenir";
}
#cuadrado {
  background: #232323;
  margin: 20px auto;
  max-width: 600px;
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

#colorDisplay {
  font-size: 200%;
}
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}

#message {
  color: black;
  display: inline-block;
  width: 20%;
}

.selected {
  background-color: steelblue;
  color: white;
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
</style>