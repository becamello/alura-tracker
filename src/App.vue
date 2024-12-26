<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <Notificacoes />
      <router-view></router-view>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Notificacoes from './components/Notificacoes.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Notificacoes
  },
  data() {
    return {
      modoEscuroAtivo: false
    }
  },
  methods: {
    trocarTema (modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }

});
</script>

<style>

.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #444444;
  --texto-inativo: #9b9b9b;
  --texto-selecionado: #FCC44D;
  --bg-tarefa: #FDCF72;
}

main.modo-escuro {
  --bg-primario: #121212;
  --texto-primario: #fff;
  --bg-tarefa: #D9A743;
}

.title, .label{
  color: var(--texto-primario) !important;
}

.conteudo {
  background-color: var(--bg-primario);
}


</style>
