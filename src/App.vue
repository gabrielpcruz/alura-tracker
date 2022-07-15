<template>
    <main class="columns is-gapless is-multiline" :class="classeModoEscuro">
        <div class="column is-one-quarter">
            <BarraLateral @alterarTema="toggleDarkMode" />
        </div>

        <div class="column is-three-quarter conteudo">
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
import {defineComponent} from 'vue';
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
            tarefas: [] as ITarefa[],
            modoEscuroAtivado: false,
            classeModoEscuro: ''
        }
    },
    computed: {
        listaEstaVazia() :boolean {
            return this.tarefas.length === 0;
        },
    },
    methods: {
        salvarTarefa(tarefa: ITarefa) {
            this.tarefas.unshift(tarefa);
        },

        toggleDarkMode(modoEscuroAtivo: boolean) {
            this.classeModoEscuro = modoEscuroAtivo ? 'modo-escuro' : '';
        }
    }
});
</script>

<style>
    .lista {
        padding: 1.25rem;
    }

    main {
        --bg-primario: #fff;
        --texto-primario: #000;
    }

    main.modo-escuro {
        --bg-primario: #2b2d42;
        --texto-primario: #ddd;
    }

    .conteudo {
        background-color: var(--bg-primario);
    }
</style>
