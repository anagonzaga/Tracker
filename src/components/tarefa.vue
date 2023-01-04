<template>
    <box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || "Tarefa sem descrição"  }}
            </div>
            <div class="column">
                <cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import cronometro from './cronometro.vue'
import iTarefa from '../interface/ITarefa'
import box from './box.vue'

export default defineComponent({
    name: 'tarefaTracker',
    components: {
         cronometro,
         box
    }, 
    props:{
        tarefa: {
            type: Object as PropType <iTarefa>,
            required: true
        }
    }
})
</script>

<style scoped>
</style>
