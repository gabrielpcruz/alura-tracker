<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                Descrição da tarefa
            </div>
            <div class="column">
                <CronometroComponent :segundos="15" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

import CronometroComponent from "@/components/CronometroComponent.vue";

export default defineComponent({
    name: "TarefaComponent",
    components: {
        CronometroComponent
    }
});
</script>

<style scoped>
    .box {
        background: #dcebff;
    }
</style>
