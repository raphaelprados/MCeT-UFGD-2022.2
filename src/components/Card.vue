<template>
  <div v-if="contrasteValidator.regular" class="card mx-auto mt-4 mb-4" :style="{height: cardHeight()}">
    <img alt="Vue logo" class="mx-auto mt-3 mb-3 ml-3 mr-3" style="width: 4rem" :src="parameters()">
    <div class="card-body card-body-regular" style="background-color: #74941c;">
      <h5 class="card-title" v-bind:style="{
        fontSize: (tamanhoFonte.regular ? '15px' :
                    tamanhoFonte.mais1 ? '17px' : '19px'),
        letterSpacing: (espacoTexto.regular ? 'normal' :
                    espacoTexto.mais1 ? '1px' : '2px')
      }">{{ cardTitle }}</h5>
    </div>
  </div>
  <div v-if="contrasteValidator.altocontrst" class="card mx-auto mt-4 mb-4 card-altocontraste" :style="{height: cardHeight()}">
    <img alt="Vue logo" class="mx-auto mt-3 mb-3 ml-3 mr-3" style="width: 4rem" :src="parameters()">
    <div class="card-body card-body-altocontraste" style="background-color: black; border-top: 1px solid white; color: white;">
      <h5 class="card-title" v-bind:style="{
        fontSize: (tamanhoFonte.regular ? '15px' :
                    tamanhoFonte.mais1 ? '17px' : '19px'),
        letterSpacing: (espacoTexto.regular ? 'normal' :
                    espacoTexto.mais1 ? '1px' : '2px')
      }">{{ cardTitle }}</h5>
    </div>
  </div>
  <div v-if="contrasteValidator.invertido" class="card mx-auto mt-4 mb-4 card-invertido" :style="{height: cardHeight()}">
    <img alt="Vue logo" class="mx-auto mt-3 mb-3 ml-3 mr-3" style="width: 4rem" :src="parameters()">
    <div class="card-body" style="background-color: #1c1b17; border-top: 1px solid #edaf05; color: #edaf05;">
      <h5 class="card-title" v-bind:style="{
        fontSize: (tamanhoFonte.regular ? '15px' :
                    tamanhoFonte.mais1 ? '17px' : '19px'),
        letterSpacing: (espacoTexto.regular ? 'normal' :
                    espacoTexto.mais1 ? '1px' : '2px')
      }">{{ cardTitle }}</h5>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        contrasteValidator: Object,
        tamanhoFonte: Object,
        espacoTexto: Object,
        imgPath: String,
        cardTitle: String
    },
    methods: {
      parameters() {
        let images = require.context('../assets/', false, /\.png$|\.jpg$/)
        return images("./" + this.imgPath)
      },
      cardHeight() {

        let height = ''

        switch(this.cardTitle) {
          case 'Biblioteca':
          case 'Cartão da UFGD':
          case 'Central de Ajuda':
          case 'Editais UFGD':
          case 'Email da UFGD': 
          case 'Seleção UFGD':
            height = 10
            break
          case 'Area restrita da Pós-Graduação':
          case 'Boletim de Serviço':
          case 'Dados Abertos UFGD':
          case 'GedWeb - Normas Técnicas':
          case 'Geração de boleto de GRU':
          case 'Gestão Portal Catedra':
          case 'SIGECAD Acadêmico':
          case 'SIGECAD Matrícula':
          case 'Sistemas de Reservas':
          case 'Validador de Documentos':
            height = 11
            break
          case 'Av. Desempenho Funcional - T. Adm.':
          case 'CAC - Central de Atendimento COIN':
          case 'Ficha catalográfica UFGD': 
            height = 12
            break
          case 'Programas de Assistencia Estudantil (mod. Acadêmico)':
          case 'SIPAC - Patrimônio, Administração e Contratos':
            height = 13
            break
          case 'SIGRH - Sistema Integrao de Gestão e de Recursos Humanos':
            height = 14
            break
        }

        height += (this.tamanhoFonte.regular ? 0 :
                    this.tamanhoFonte.mais1 ? 1 : 2)

        return (height + 'rem')
      }
    }
}
</script>

<style scoped>
    .card {
        border: 1px solid gray;
        text-align: center;
        width: 10rem;
        height: 10rem;
        cursor: pointer;
    }
    .card-body {
        border-bottom-left-radius: 6px;
        border-bottom-right-radius: 6px;
        height: 10rem;
        color: white;
    }
    .card-body-regular {
      border: 1px solid gray;
      background-color: #74941c;
    }
    .card-altocontraste {
      border: 1px solid white;
      background-color: black;
    }
    .card-invertido {
      border: 1px solid #edaf05;
      background-color: #1c1b17;
    }
    .card-body-altocontraste {
      border: 1px solid white;
      background-color: black;
    }
    .card-body-invertido {
      border: 1px solid #edaf05; 
      background-color: #1c1b17; 
      color: #edaf05;
    }
    .card-body {
        background: #d3d8e0;
    }
    .h5 .mais1 {
      font-size: 24px;
    }
    .h5 .mais2 {
      font-size: 36px;
    }
    .h5 .reg {
      font-size: 16px;
    }

</style>