<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroComponent
            :segundos="this.segundos"
        />

        <BotaoComponent
            label="play"
            icon="fa-play"
            @metodo="iniciar"
            :cronometro-ativo="cronometroAtivo"
        />

        <BotaoComponent
            label="stop"
            icon="fa-stop"
            @metodo="finalizar"
            :cronometro-ativo="!cronometroAtivo"
        />
    </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";

import CronometroComponent from "@/components/CronometroComponent.vue";
import BotaoComponent from "@/components/BotaoComponent.vue"

export default defineComponent({
    name: 'TemporizadorComponent',
    emits: [
            'aoTemporizadorFinalizado'
    ],
    components: {
        CronometroComponent,
        BotaoComponent
    },
    data() {
        return {
            segundos: 0,
            cronometro: 0,
            cronometroAtivo: false
        }
    },

    methods: {
        iniciar() {
            this.cronometro = setInterval(() => {
                this.segundos += 1;
            }, 1000);

            this.cronometroAtivo = true;
        },

        finalizar() {
            clearInterval(this.cronometro);

            this.cronometroAtivo = false;

            this.$emit('aoTemporizadorFinalizado', this.segundos);

            this.segundos = 0;
        }
    }
});

</script>

<style scoped>

</style>
