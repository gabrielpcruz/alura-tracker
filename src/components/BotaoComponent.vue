<template>
    <button class="button" @click="metodo" :disabled="cronometroAtivo">
            <span class="icon">
                <i class="fas" :class="icon"></i>
            </span>
        <span>{{ label }}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "BotaoComponent",
    emits: ['metodo'],
    props: {
        cronometroAtivo: Boolean,
        icon: String,
        label: String
    },
    methods: {
        metodo() {
            this.$emit('metodo')
        }
    }
})
</script>

<style scoped>

</style>
