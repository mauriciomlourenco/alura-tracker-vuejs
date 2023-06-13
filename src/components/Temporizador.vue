<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroForm :tempoEmSegundos="tempoEmSegundos" />
                    <!-- Versão antiga, Desafio curso componentizar botões
                    <button class="button" @click="iniciar" :disabled="cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>

                    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                    -->

                    <ButtonTemporizador 
                        nomeBotao="play"
                        iconeBotao="fa fa-play" 
                        :botaoAtivo="cronometroRodando"
                        @clicado="iniciar"  
                    />

                    <ButtonTemporizador 
                        nomeBotao="stop"
                        iconeBotao="fa fa-stop" 
                        :botaoAtivo="!cronometroRodando"
                        @clicado="finalizar"  
                    />
                </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroForm from './Cronometro.vue';
import ButtonTemporizador from './ButtonTemporizador.vue';

export default defineComponent({
    name: 'TemporizadorTarefa',
    emits: ['aoTemporizadorFinalizado'],
    components: {
        CronometroForm,
        ButtonTemporizador
    },
    data () {
        return {            
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false,
        }
    },    
    methods: {
        iniciar() {
            // começar a contagem
            // 1 seg = 1000 ms
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => { 
                this.tempoEmSegundos += 1;
            }, 1000);
        },

        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    }
})
</script>

<style>
</style>