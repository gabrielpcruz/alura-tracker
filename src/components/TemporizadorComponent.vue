<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <Cronometro
            :segundos="this.segundos"
        />

        <button class="button" @click="iniciar" :disabled="cronometroAtivo">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>

        <button class="button" @click="finalizar" :disabled="!cronometroAtivo">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script>
import {defineComponent} from "vue";

import Cronometro from "@/components/CronometroComponent";

export default defineComponent({
    name: 'TemporizadorComponent',
    components: {
        Cronometro
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
            this.segundos = 0;

            this.cronometroAtivo = false;
        }
    }
});

</script>

<style scoped>

</style>
