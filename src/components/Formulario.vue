<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input 
                    type="text" 
                    class="input" 
                    placeholder="Qual tarefa você deseja iniciar ?"
                    v-model="descricaoTarefa"
                >
            </div>

            <div class="column">
                <TemporizadorTarefa @aoTemporizadorFinalizado="finalizarTarefa"/>

            </div>

        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTarefa from './Temporizador.vue';

export default defineComponent({
    name: 'FormularioTarefa',
    emits: ['aoSalvarTarefa'],
    components: {
        TemporizadorTarefa
    },
    data () {
        return {
            descricaoTarefa: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number) : void {
           //console.log("Tempo descorrido:", tempoDecorrido)
           //console.log("Tarefa:", this.descricaoTarefa)
           this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricaoTarefa
           })
           this.descricaoTarefa = ''; 
        }
    }    
})
</script>

<style>
    .formulario {
        color: var(--texto-primario);
        background-color: var(--bg-primario);
    }
</style>