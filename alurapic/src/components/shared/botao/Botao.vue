<template>
  <button class="botao" :class="estiloDoBotao" :type="tipo" @click="disparaAcao()">
    {{ rotulo }}
  </button>
</template>

<script>
export default {
  props: {
    tipo: {
      required: true,
      type: String
    },

    rotulo: {
      required: true,
      type: String
    },

    confirmacao: {
      required: false,
      default: false,
      type: Boolean
    },

    estilo: {
      required: false,
      default: 'padrao',
      type: String
    }
  },
   methods: {
    disparaAcao() {
      if(this.confirmacao) {
        if(confirm('Confirma operacao?')) {
          this.$emit('botaoAtivado');
        }
        return;
      }
      this.$emit('botaoAtivado');
    }
   },
   computed: {
     estiloDoBotao() {
      if(this.estilo == 'padrao') return 'botao-padrao';
      if(this.estilo == 'perigo') return 'botao-perigo';
     }
   }
}
</script>

<style lang="sass" scoped>

  @import './Botao.scss';

</style>
