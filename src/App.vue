<template>
	<div id="app">
		<h1>Tarefas</h1>
		<NovaTarefa @tarefaAdc="adicionarTrf"/>
		<Progresso :progresso="progresso" />
		<ListaTarefas :tarefas="tarefas" @tarefaDeletada="deletarTrf" @estadoTrfMudou="alternarTrf"/>
	</div>
</template>

<script>
import Progresso from './components/Progresso.vue'
import ListaTarefas from './components/ListaTarefas.vue'
import NovaTarefa from './components/NovaTarefa'
export default {
	components: {
		ListaTarefas,
		NovaTarefa,
		Progresso
	},
	data () {
		return {
			tarefas: []
		}
	},
	computed: {
		progresso() {
			const total = this.tarefas.length
			const feito = this.tarefas.filter(t => !t.pendente).length

			return Math.round(feito / total * 100) || 0
		}
	
	},
	watch: {
		tarefas: {
			deep: true,
			handler() {
				localStorage.setItem('tarefas', JSON.stringify(this.tarefas))
			}
		}
	},
	methods: {
		adicionarTrf(tarefa) {
			const mesmoNome = t => t.nome === tarefa.nome
			const novaTarefa = this.tarefas.filter(mesmoNome).length == 0

			if(novaTarefa && tarefa.nome != ''){
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
	},
	created() {
		const json = localStorage.getItem('tarefas')
		const array = JSON.parse(json)
		this.tarefas = Array.isArray(array) ? array : []
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
