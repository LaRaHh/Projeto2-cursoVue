<template>
    <div class="listaTarefas">
        <template v-if="tarefas.length">
            <Tarefa v-for="tarefa in tarefas" :key="tarefa.nome" :tarefa="tarefa">
            </Tarefa>
        </template>
        <p v-else class="sem-tarefa">Sem ter o que fazer?? Adicione uma tarefa</p>
    </div>
</template>

<script>
import Tarefa from './Tarefa.vue'
export default {
    name: 'ListaTarefas',
    components: {
        Tarefa
    },
    props: {
        tarefas: {type: Array, required: true}
    }
}
</script>

<style>
    .listaTarefas{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .listaTarefas .tarefa{
        margin: 10px;
    }

    .sem-tarefa{
        color: #AAA;
        font-size: 1.7rem;
    }
</style>