<template>
    <div @click="$emit('estadoTrfMudou', tarefa)" class="tarefa" :class="estadoTarefa" >
        <span class="fechar" @click.stop="$emit('tarefaDeletada', tarefa)">x</span>
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
    .tarefa{
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 10px;
        border-radius: 8px;
        font-size: 2rem;
        font-weight: 300;
        cursor: pointer;
        user-select:none;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 5px;
    }

    .pendente {
        border-left: 12px solid #B73229;
        background-color: #F44336;
    }

    .feito{
        color: #DDD;
        border-left: 12px solid #0A8f08;
        background-color: #4CAF50;
        text-decoration: line-through;
    }

    .pendente .fechar{
        background-color: #B73229;
    }

    .feito .fechar{
        background-color:  #0A8f08;
    }

    .fechar{
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 0.9rem;
        font-weight: 600;
        height: 20px;
        width: 20px;
        border-radius: 10px;

        display: flex;
        justify-content: center;
    }
</style>