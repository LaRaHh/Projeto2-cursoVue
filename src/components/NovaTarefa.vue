<template>
    <div class="nova-tarefa">
        <input type="text" v-model="nome" @keydown.enter="adicionar" placeholder="Nova tarefa" class="el-formulario">
        <button  @click="adicionar" class="el-formulario">+</button>
    </div>
</template>

<script>
export default {
    name: 'NovaTarefa',
    data() {
        return{
            nome:''
        }
    },
    methods: {
        adicionar() {
            this.$emit('tarefaAdc', {nome: this.nome})
            this.nome=''
        }
    }
}
</script>

<style>
    .nova-tarefa{
        padding: 35px;
    }

    .el-formulario{
        outline: none;
        font-size: 2rem;
        border: 1px solid #FFF;
        padding: 5px 10px 5px 10px;
        color: #FFF;
    }
    input.el-formulario{
        width: 500px;
        background-color: #FFF2;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }

    button.el-formulario{
        border-left: none;
        background-color: rgba(32, 114, 236, 0.788);
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
    }
</style>