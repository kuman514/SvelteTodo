<script>
	import Todo from './Todo.svelte';
	import { writable } from 'svelte/store';

	let title = '';
	let todos = writable([]);
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

		if (title.trim() === '') {
			title = '';
			return;
		}

		// In Svelte, to activate reactivity, reallocate itself.
		$todos.push({
			id,
			title
		});
		$todos = $todos;
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
{#each $todos as todo}
	<!-- todos, not $todos, to send a store object -->
	<Todo {todos} {todo} />
{/each}

<style>
	button {
		background-color: aliceblue;
	}
</style>
