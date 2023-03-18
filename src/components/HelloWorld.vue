
<template>
  <div class="d-flex flex-row"></div>
  <div class="d-flex flex-row flex-wrap mx-2">
      <Card v-for="modulo in modulos" v-bind:key="modulo.path" :contrasteValidator="contrasteValidator" :tamanhoFonte="tamanhoFonte" :espacoTexto="espacoTexto" 
            :imgPath="modulo.path" :cardTitle="modulo.moduleName"/>
  </div>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
  name: 'HelloWorld',
  props: {
    contrasteValidator: Object,
    tamanhoFonte: Object,
    espacoTexto: Object
  },
  data() {
    return {
      modulos: [
        { path: 'area_restrita_pos_grad.png', moduleName: 'Area restrita da Pós-Graduação'},
        { path: 'avl_desemp_func.png', moduleName: 'Av. Desempenho Funcional - T. Adm.'},
        { path: 'biblioteca.png', moduleName: 'Biblioteca'},
        { path: 'boltm_serv.png', moduleName: 'Boletim de Serviço'},
        { path: 'cac.png', moduleName: 'CAC - Central de Atendimento COIN'},
        { path: 'cartao.png', moduleName: 'Cartão da UFGD'},
        { path: 'central_ajd.png', moduleName: 'Central de Ajuda'},
        { path: 'dados_abertos.png', moduleName: 'Dados Abertos UFGD'},
        { path: 'editais.png', moduleName: 'Editais UFGD'},
        { path: 'email.png', moduleName: 'Email da UFGD'},
        { path: 'ficha_catalo.png', moduleName: 'Ficha catalográfica UFGD'},
        { path: 'normas_tecnicas.png', moduleName: 'GedWeb - Normas Técnicas'},
        { path: 'boleto_gru.png', moduleName: 'Geração de boleto de GRU'},
        { path: 'gestao_catedra.png', moduleName: 'Gestão Portal Catedra'},
        { path: 'assist_estdantl.png', moduleName: 'Programas de Assistencia Estudantil (mod. Acadêmico)'},
        { path: 'selecao.png', moduleName: 'Seleção UFGD'},
        { path: 'academico_matricula.png', moduleName: 'SIGECAD Acadêmico'},
        { path: 'academico_matricula.png', moduleName: 'SIGECAD Matrícula'},
        { path: 'sigrh.png', moduleName: 'SIGRH - Sistema Integrao de Gestão e de Recursos Humanos'},
        { path: 'sipac.png', moduleName: 'SIPAC - Patrimônio, Administração e Contratos'},
        { path: 'sist_reservas.png', moduleName: 'Sistemas de Reservas'},
        { path: 'avl_desemp_func.png', moduleName: 'Validador de Documentos'}
      ]
    }
  },
  components: {
    Card
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
