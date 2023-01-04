<template>
  <main class="columns is-galpless is-multiple" :class="{'modo-escuro' : modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <barraLateral @temaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <formulario @salvarTarefa="salvarTarefa" />
      <div class="lista">
          <tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
          <box v-if="listaEstaVazia">
            Você não está muito produtivo hoje <span class="icon"><i class="fa-solid fa-face-sad-tear fa-lg"></i></span>
          </box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import barraLateral from './components/barraLateral.vue'
import formulario from './components/formulario.vue'
import tarefa from './components/tarefa.vue'
import iTarefa from './interface/ITarefa'
import box from './components/box.vue' 

export default defineComponent({
  name: 'App',
  components: {
    barraLateral,
    formulario, 
    tarefa, 
    box
  },
  data() {
    return {
      tarefas: [] as iTarefa[],
      modoEscuroAtivo:false
    }
  }, 
  computed:{
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: iTarefa){
      this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo: boolean){
        this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
  .lista{
    padding: 1.25rem;
  }
  main{
    --bg-primario: #fff;
    --text-primario: #000;
  }
  main.modo-escuro{
    --bg-primario: #4A587D;
    --text-primario: #ddd;
  }
  .conteudo{
    background-color: var(--bg-primario)
  }
</style>
