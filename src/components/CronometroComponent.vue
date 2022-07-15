<template>
    <section>
        <strong class="display">{{ tempoDecorrido }}</strong>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from "vue";

    export default defineComponent({
        name: 'CronometroComponent',
        props: {
            segundos: {
                type: Number,
                default: 0
            }
        },
        computed: {
            tempoDecorrido () : string {
                if (this.segundos === 0) {
                    return '00:00:00';
                }

                return new Date(this.segundos * 1000)
                        .toISOString()
                        .substr(11,8)
            }
        }
    })
</script>

<style scoped>
    .display {
        color: var(--texto-primario);
    }
</style>
