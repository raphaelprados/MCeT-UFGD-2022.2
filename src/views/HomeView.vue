<template>
  <div v-bind:style="{ backgroundColor: 
                        (contrasteValidator.regular ? '#e3e4e8' : 
                            contrasteValidator.altocontrst ? 'black' : '#1c1b17'),
                         color: (contrasteValidator.regular ? 'black' : 
                            contrasteValidator.altocontrst ? 'white' : 'white'),
                         fonteSize: (tamanhoFonte.regular ? 16 + 'px' : 
                            tamanhoFonte.mais1 ? 24 + 'px' : 32 + 'px') }">
      <Navbar @clicked="onClickChild" @clickedTam="onClickTamanho" @clickedEsp="onClickEspaco"/>
      <HelloWorld :contrasteValidator="contrasteValidator" :tamanhoFonte="tamanhoFonte" :espacoTexto="espacoFonte"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Navbar from '@/components/Navbar.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Navbar
  },
  data() {
    return {
      contraste: 0,
      contrasteValidator: {
        regular: true,
        altocontrst: false,
        invertido: false,
        string: ""
      },
      tamanhoFonte: {
        regular: true,
        mais1: false,
        mais2: false,
        string: ""
      },
      espacoFonte: {
        regular: true,
        mais1: false,
        mais2: false,
        string: ""
      }
    }
  },
  methods: {
    onClickChild(value) {
      // this.contraste = value
      this.contrasteValidator = value
    },
    onClickTamanho(value) {
      // this.contraste = value
      this.tamanhoFonte = value
      console.log(this.tamanhoFonte.regular)
    },
    onClickEspaco(value) {
      // this.contraste = value
      this.espacoFonte = value
    }
  }
}
</script>

<style>
  .regular {
    background-color: #e3e4e8;
  }
  .altocontraste {
    background-color: black;
  }
  .invertido {
    background-color: #1c1b17;
  }
</style>
