<template>
    <main class="columns is-gapless is-multiline">
        <div class="column is-one-quarter">
            <BarraLateral />
        </div>

        <div class="column is-three-quarter">
            <Formulario @aoSalvarTarefa="salvarTarefa" />
            <div class="lista">
                <TarefaComponent
                    v-for="(tarefa, index) of this.tarefas" :key="index"
                    :tarefa="tarefa"
                />

                <BoxComponent v-show="listaEstaVazia">
                    Você não está muito produtivo hoje :(
                </BoxComponent>
            </div>
        </div>
    </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from "@/components/BarraLateral.vue";
import Formulario from "@/components/Formulario.vue";
import TarefaComponent from "@/components/Tarefa.vue";
import ITarefa from "@/interfaces/ITarefa";
import BoxComponent from "@/components/BoxComponent.vue";

export default defineComponent({
    name: 'App',
    components: {
        BoxComponent,
        TarefaComponent,
        BarraLateral,
        Formulario
    },
    data() {
        return {
            tarefas: [] as ITarefa[]
        }
    },
    computed: {
        listaEstaVazia() :boolean {
            return this.tarefas.length === 0;
        }
    },
    methods: {
        salvarTarefa(tarefa: ITarefa) {
            this.tarefas.unshift(tarefa);
        }
    }
});
</script>

<style>
    .lista {
        padding: 1.25rem;
    }
</style>
