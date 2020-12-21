<template>
    <div class="tarefa" :class="estadoTarefa">
        <p>{{ tarefa.nome }}</p>
    </div>
</template>

<script>
export default {
    name: 'Tarefa',
    props: {
        tarefa: { type: Object, required: true}
    },
    computed: {
        estadoTarefa() {
            return {
                pendente: this.tarefa.pendente,
                feito: !this.tarefa.pendente
            }
        }
    }
    
}
</script>

<style>

</style>