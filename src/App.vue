<template>
	<div id="app">
		<h1>Tarefas</h1>
		<NovaTarefa @tarefaAdc="adicionarTrf"/>
		<ListaTarefas :tarefas="tarefas" @tarefaDeletada="deletarTrf" @estadoTrfMudou="alternarTrf"/>
	</div>
</template>

<script>
import ListaTarefas from './components/ListaTarefas.vue'
import NovaTarefa from './components/NovaTarefa'
export default {
	components: {
		ListaTarefas,
		NovaTarefa
	},
	data () {
		return {
			tarefas: []
		}
	},
	methods: {
		adicionarTrf(tarefa) {
			const mesmoNome = t => t.nome === tarefa.nome
			const novaTarefa = this.tarefas.filter(mesmoNome).length == 0

			if(novaTarefa){
				this.tarefas.push({
					nome: tarefa.nome,
					pendente: tarefa.pendente || true
				})
			}
		},
		deletarTrf(i) {
			this.tarefas.splice(i, 1)
		},
		alternarTrf(i) {
			this.tarefas[i].pendente = !this.tarefas[i].pendente
		}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
