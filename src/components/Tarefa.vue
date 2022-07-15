<template>
    <BoxComponent>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column cronometro">
                <CronometroComponent :segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxComponent>
</template>

<script lang="ts">
    import {defineComponent, PropType} from "vue";

    import ITarefa from "@/interfaces/ITarefa";
    import CronometroComponent from "@/components/CronometroComponent.vue";
    import BoxComponent from "@/components/BoxComponent.vue";

    export default defineComponent({
        name: "TarefaComponent",
        components: {
            BoxComponent,
            CronometroComponent
        },
        props: {
            tarefa: {
                type: Object as PropType<ITarefa>,
                required: true
            },
        }
    });
</script>

<style scoped>

</style>
