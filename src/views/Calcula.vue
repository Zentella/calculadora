<template>
  <div class="text-center fondo">
    <h6>calc</h6>
    <v-row>
      <v-col v-model="screen">
        <h1 class="cuadro">{{ pantalla }}</h1>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-function </v-icon> -->
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-alpha-c </v-icon> -->
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-code-less-than </v-icon> -->
        </v-btn>

        <v-btn @click="c" class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-percent-outline </v-icon> -->
          <v-icon dark> mdi-alpha-c </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-exponent </v-icon> -->
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-format-superscript </v-icon> -->
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <!-- <v-icon dark> mdi-square-root </v-icon> -->
        </v-btn>

        <v-btn
          @click="divi"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark> mdi-division </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 7"> mdi-numeric-7 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 8"> mdi-numeric-8 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 9"> mdi-numeric-9 </v-icon>
        </v-btn>

        <v-btn @click="por" class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-close </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 4"> mdi-numeric-4 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 5"> mdi-numeric-5 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 6"> mdi-numeric-6 </v-icon>
        </v-btn>

        <v-btn
          @click="resta"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark> mdi-minus </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 1"> mdi-numeric-1 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 2"> mdi-numeric-2 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 3"> mdi-numeric-3 </v-icon>
        </v-btn>

        <v-btn
          @click="suma"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark> mdi-plus </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn
          :disabled="!neg"
          @click="neg = false"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark @click="num = '-'"> mdi-plus-minus-variant </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 0"> mdi-numeric-0 </v-icon>
        </v-btn>

        <v-btn
          :disabled="!punto"
          @click="punto = false"
          class="mx-2"
          fab
          dark
          small
          color="primary"
        >
          <v-icon dark @click="num = '.'"> mdi-decimal </v-icon>
        </v-btn>

        <v-btn
          @click="igual"
          class="mx-2"
          fab
          dark
          small
          color="green darken-2"
        >
          <v-icon dark @click="sum = 1"> mdi-equal </v-icon>
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'Calcula',

  data: () => ({
    pantalla: '',
    num: '',
    punto: false,
    neg: true,
    n1: '', // 0
    opera: null,
    flag: 0,
    sum: 0,
    inicio: 0
    // dec: 0
  }),

  computed: {
    screen() {
      console.log('* screen') //
        console.log('punto ', this.punto)

      if (this.opera == null) {
        this.concatenar()
      }

      if (this.opera == 'suma') {
        this.concatenar()
        console.log('ahora sumar')
        console.table(' pantalla, n1 , num', [this.pantalla, this.n1, this.num]) //
        if (this.punto == false) {
          console.log('this.pantalla, this.punto', this.pantalla, this.punto)
          this.punto = true
        } else if (this.sum == 0) {
          // aun no click en =
          // this.pantalla = parseFloat(this.num)  // ojo
          console.log(' sum 0, pantalla, punto', this.pantalla, this.punto)
        }
      }

      if (this.opera == 'resta') {
        this.concatenar()
        console.log('ahora restar')
      }

      if (this.opera == 'por') {
        this.concatenar()
        console.log('ahora multiplicar')

        console.log(
          'pantalla this.num this.n1 ',
          this.pantalla,
          this.num,
          this.n1
        )
      }

      if (this.opera == 'divi') {
        this.concatenar()
        console.log('ahora dividir')

        console.log(
          'pantalla this.num this.n1 ',
          this.pantalla,
          this.num,
          this.n1
        )
      }

      // pantalla
      console.table(' pantalla, n1 , num', [this.pantalla, this.n1, this.num]) //

      if (this.num == '-') {
        this.pantalla = this.num
      }
    }
  },

  methods: {
    concatenar() {
      console.log('concatenar')

      console.table(' pantalla, n1 , num', [this.pantalla, this.n1, this.num]) //

      if (this.inicio == 1) {
        this.pantalla = this.pantalla + this.num // concatenar // this.pantalla = 0 + parseFloat(this.num)
        this.num = ''
        console.log('2º paso inicio=1')
        console.table(' pantalla, n1 , num', [this.pantalla, this.n1, this.num]) //
      } else {
        console.log('1º paso')
        this.pantalla = this.num
        if (this.num != '') {
          this.inicio = 1
          this.punto = true
        }
      }
    },

    igual() {
      this.neg = true
      console.log('igual')
      console.table(' pantalla, n1 , num', [this.pantalla, this.n1, this.num]) //
      this.punto = true

      if (this.opera == 'resta') {
        this.pantalla = this.n1 - this.pantalla // parseFloat(this.pantalla) - this.n1 // aca cambia 0
        console.log('this.pantalla igual ', this.pantalla) // 0-3
        this.flag = 0
      }

      if (this.opera == 'suma') {
        if (this.sum == 0) {
          this.pantalla = 0
        }
        if (this.pantalla == '') {
          this.pantalla = 0
        }
        this.pantalla = parseFloat(this.n1) + parseFloat(this.pantalla) // ok
        this.n1 = 0
        console.log('suma pantalla n1', this.pantalla, this.n1) // 7 0
      }

      if (this.opera == 'por') {
        if (this.pantalla == '') {
          this.pantalla = 1
        }
        this.pantalla = parseFloat(this.n1) * parseFloat(this.pantalla)
        this.n1 = 0
        console.log('por pantalla n1', this.pantalla, this.n1)
      }

      if (this.opera == 'divi') {
        if (this.pantalla == '') {
          this.pantalla = 1
        }
        this.pantalla = parseFloat(this.n1) / parseFloat(this.pantalla)
        this.n1 = 0
        console.log('divi pantalla n1', this.pantalla, this.n1)
      }
    },

    suma() {
      this.opera = 'suma'
      this.punto = true
      this.inicio = 0

      this.n1 = this.pantalla

      console.log('suma n1 ', this.n1) // vacio
      console.log('inicio ', this.inicio)
    },

    resta() {
      this.opera = 'resta'
      this.punto = true
      this.inicio = 0

      this.n1 = this.pantalla

      if (this.flag == 1) {
        console.log('flag 1 ')
      } else {
        console.log('flag 0 ')

        this.flag = 1
      }

      console.log('resta n1 ', this.n1)
    },

    por() {
      this.opera = 'por'
      this.punto = true
      this.inicio = 0

      this.n1 = this.pantalla

      console.log('por n1', this.n1) // 3 1
    },

    divi() {
      this.opera = 'divi'
      this.punto = true
      this.inicio = 0

      this.n1 = this.pantalla

      console.log('divide n1', this.n1) // 3 1
    },

    c() {
      console.log('c')
      this.pantalla = ''
      this.n1 = ''
      this.num = ''
      this.opera = null
      this.flag = 0
      this.inicio = 0
      this.punto = false
      this.neg = true
    }
  }
}
</script>

<style scoped>
.cuadro {
  border: 2px solid black;
  height: 50px;
}
.fondo {
  background: grey;
  padding-bottom: 80%;
}
</style>
