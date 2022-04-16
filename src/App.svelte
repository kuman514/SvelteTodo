<script>
	import Todo from './Todo.svelte';

	let title = '';
	let todos = [];
	let id = 0;

	function createTodo() {
		/*
		const newTodos = Array.from(todos);
		newTodos.push({
			id,
			title
		});
		todos = newTodos;
		*/
		// Svelte에서는 자기자신을 할당하는 것이 반응성을 살리는 것이라 일반적이다?
		todos.push({
			id,
			title
		});
		todos = todos;
		title = '';
		id++;
	}
</script>

<input
	type="text"
	bind:value={title}
	on:keydown={event => {
		if (event.key === 'Enter') {
			createTodo();
		}
	}}
/>
<button on:click={createTodo}>
	Create Todo
</button>
{#each todos as todo}
	<Todo {todo} />
{/each}

<style>
	button {
		background-color: aliceblue;
	}
</style>
