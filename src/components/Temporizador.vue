<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroTarefa :tempoEmSegundos="tempoEmSegundos" />
        <Botao icone="fas fa-play" :desabilitado="isCronometroRodando" texto="Começar" @clicado="iniciar"/>
        <Botao icone="fas fa-stop" :desabilitado="!isCronometroRodando" texto="Parar" @clicado="finalizar"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Botao from './Botao.vue';
import CronometroTarefa from './Cronometro.vue'

export default defineComponent({
    name: 'TemporizadorComponent',
    emits: ['aoTemporizadorFinalizado'],
    components: {
    CronometroTarefa,
    Botao
},
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            isCronometroRodando: false,
        }
    },
    methods: {
        iniciar() {
            this.isCronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000)
        },
        finalizar() {
            this.isCronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>