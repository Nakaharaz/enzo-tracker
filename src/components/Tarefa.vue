<template>
    <Box class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <CronometroTarefa :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import Box from './Box.vue';
import CronometroTarefa from './Cronometro.vue';

export default defineComponent({
    name: "TarefaComponent",
    components: {
    CronometroTarefa,
    Box
},
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        }
    }
}) 
</script>
