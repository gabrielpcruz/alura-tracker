<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input
                    type="text"
                    class="input"
                    placeholder="Qual tarefa você deseja iniciar?"
                >
            </div>

            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <Cronometro
                        :segundos="this.segundos"
                    />

                    <button class="button" @click="iniciar">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>

                    <button class="button" @click="finalizar">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import { defineComponent } from "vue";
    import Cronometro from "@/components/CronometroComponent";

    export default defineComponent({
        name: 'FormularioComponent',
        components: {
            Cronometro
        },
        data() {
          return {
              segundos: 0,
              cronometro: 0
          }
        },
        methods: {
            iniciar() {
                this.cronometro = setInterval(() => {
                    this.segundos += 1;
                }, 1000);
            },

            finalizar() {
                clearInterval(this.cronometro);
                this.segundos = 0;
            }
        }
    });
</script>

<style scoped>

</style>
