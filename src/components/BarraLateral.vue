<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button" @click="alterarTema">
           {{  textoBotao }}
        </button>
    </header>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'BarraLateral',
        emits: ['aoTemaAlterado'],
        data() {
            return {
                modoEscuroAtivo: false,
            }

        },
        computed: {
            textoBotao () {
                if(this.modoEscuroAtivo){
                    return 'Desativar modo escuro'
                }

                return 'Ativar modo escuro'
            }
        },
        methods: {
            alterarTema () {
                this.modoEscuroAtivo = !this.modoEscuroAtivo;
                this.$emit('aoTemaAlterado', this.modoEscuroAtivo);
            }
        }
    })

</script>

<style>
    /* todo o estilo do componente */
    header {
        background: #0d3b66;
        width: 100%;
        height: 100vh;

        padding: 1rem;

        display: flex;
        flex-direction: column;
        align-items: center;
    }

    @media only screen and (max-width: 786px){
        header {
            padding: 2.5rem;
            height: auto;
        }
    }
</style>