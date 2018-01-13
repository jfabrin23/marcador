<template>
  <div class="home">
    <Header/>
    <main class="container row wrap justify-center">
      <div class="time1 flex" @click="time = 1">
        <div class="container row wrap center">
          <h3 class="flex">Nós</h3>
          <div class="flex" v-if="time === 1">
            <img src="../assets/check.png">
          </div>
        </div>

        <div class="container column">
          <div v-for="item in items">
            <label class="tento" >{{item.label}}
              <input type="radio" id="one" v-bind:value="item.valor" v-model="tento.time1" name="time1" disabled>
              <span class="checkmark"></span>
            </label>
          </div>
        </div>
      </div>
      <div class="time2 flex" @click="time = 2">
        <div class="container row wrap center">
          <h3 class="flex">Eles</h3>
          <div class="flex" v-if="time === 2">
            <img src="../assets/check.png">
          </div>
        </div>

        <div class="container column">
          <div v-for="item in items">
            <label class="tento" >{{item.label}}
              <input type="radio" id="one" v-bind:value="item.valor" v-model="tento.time2" name="time2" disabled>
              <span class="checkmark"></span>
            </label>
          </div>
        </div>
      </div>
      <div class="config basis1">
        <div class="container row wrap justify-center btnTento">
          <button class="flex" @click="somaTento(1)">1 Tento</button>
        </div>
        <div class="container row wrap justify-center btnTento">
          <button class="flex" @click="somaTento(3)">Truco!</button>
        </div>
        <div class="container row wrap justify-center btnTento">
          <button class="flex" @click="somaTento(6)">6 Tento!</button>
        </div>
        <div class="container row wrap justify-center btnTento">
          <button class="flex" @click="somaTento(9)">Yah! 9!</button>
        </div>
        <div class="container row wrap justify-center btnTento">
          <button class="flex" @click="somaTento(12)">12 Paus!</button>
        </div>

        <div class="container row wrap justify-center btnTento">
          <button class="flex" @click="reset()">Novo Jogo</button>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import Header from '@/components/Header'

export default {
  components: {
    Header
  },
  data () {
    return {
      tento: {
        time1: 0,
        time2: 0
      },
      time: 1,
      items: [
        {
          label: 0,
          valor: 0
        },
        {
          label: 1,
          valor: 1
        },
        {
          label: 2,
          valor: 2
        },
        {
          label: 3,
          valor: 3
        },
        {
          label: 4,
          valor: 4
        },
        {
          label: 5,
          valor: 5
        },
        {
          label: 6,
          valor: 6
        },
        {
          label: 7,
          valor: 7
        },
        {
          label: 8,
          valor: 8
        },
        {
          label: 9,
          valor: 9
        },
        {
          label: 10,
          valor: 10
        },
        {
          label: 11,
          valor: 11
        },
        {
          label: 12,
          valor: 12
        }
      ]
    }
  },
  methods: {
    somaTento (valor) {
      let inVitoria = false
      if (this.time === 1) {
        this.tento.time1 = this.tento.time1 + valor
        if (this.tento.time1 >= 12) {
          inVitoria = true
        }
      } else {
        this.tento.time2 = this.tento.time2 + valor
        if (this.tento.time2 >= 12) {
          inVitoria = true
        }
      }

      if (inVitoria) {
        this.$swal('Fim de Jogo!')
        this.reset()
      }
    },
    reset () {
      this.tento.time1 = 0
      this.tento.time2 = 0
    }
  }
}
</script>

<style>
main {
  width: 100vw;
}
.time1 {
  height: 85vh;
  padding-left: 3vw;
  padding-right: 3vw;
}
.time2 {
  height: 85vh;
  background-color: var(--corSecundaria);
  padding-left: 3vw;
  padding-right: 3vw;
}

button {
  width: 15vw;
  height: 8vh;
  border-radius: 1vw;
  background-color: var(--corVerdeLink);
  border: none;
  font-size: 2vh;
  color: var(--corSecundaria);
}
button:active {
  background-color: var(--corVerdeHover);
  color: var(--corRodape);
}

.tento {
    display: block;
    position: relative;
    padding-left: 35px;
    margin-bottom: 12px;
    cursor: pointer;
    font-size: 18px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

/* Hide the browser's default checkbox */
.tento input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
}

/* Create a custom checkbox */
.checkmark {
    position: absolute;
    top: 0;
    left: 0;
    height: 25px;
    width: 25px;
    background-color: var(--tentoColor);
}

/* On mouse-over, add a grey background color */
.tento:hover input ~ .checkmark {
    background-color: var(--corTextoHover);
}

/* When the checkbox is checked, add a blue background */
.tento input:checked ~ .checkmark {
    background-color: var(--corVerdeLink);
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
    content: "";
    position: absolute;
    display: none;
}

/* Show the checkmark when checked */
.tento input:checked ~ .checkmark:after {
    display: block;
}

/* Style the checkmark/indicator */
.tento .checkmark:after {
    left: 9px;
    top: 5px;
    width: 5px;
    height: 10px;
    border: solid white;
    border-width: 0 3px 3px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
}

.config {
  padding: 5vw;
}
.btnTento {
  padding-bottom: 2vh;
}
</style>