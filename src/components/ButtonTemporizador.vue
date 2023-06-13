<template>
    <button class="button" @click="clicado" :disabled="botaoAtivo">
        <span class="icon">
            <i :class="iconeBotao"> </i>
        </span>
        <span>{{  nomeBotao }}</span>
    </button>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'ButtonTemporizador',
        emits: ['clicado'],
        props: {
            nomeBotao: {
                type: String,
                default: ''
            },
            iconeBotao: {
                type: String,
                default: ''
            },
            botaoAtivo:{
                type: Boolean,
                default: false,
            },
            funcaoBotao: {
                type: Function
            }
        },
        methods: {
            clicado() : void {
                this.$emit('clicado');
            }
        }
    });
</script>

<script>
</script>