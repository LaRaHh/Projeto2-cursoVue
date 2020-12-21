<template>
	<div id="app">
		<h1>Tarefas</h1>
		<ListaTarefas :tarefas="tarefas"/>
	</div>
</template>

<script>
import ListaTarefas from './components/ListaTarefas.vue'
export default {
	components: {
		ListaTarefas
	},
	data () {
		return {
			tarefas: [
				{nome: 'Fazer atividade física', pendente: true},
				{nome: 'Trocar corda do violão', pendente: false}
			]
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
