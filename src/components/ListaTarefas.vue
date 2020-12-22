<template>
    <div class="lista-tarefas">
        <template v-if="tarefas.length">
            <Tarefa v-for="(tarefa, i) in tarefas" :key="tarefa.nome" :tarefa="tarefa" @tarefaDeletada="$emit('tarefaDeletada', i)">
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
    .lista-tarefas{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .lista-tarefas .tarefa{
        margin: 10px;
    }

    .sem-tarefa{
        color: #AAA;
        font-size: 1.7rem;
    }
</style>