<script>
	let todos = [
		{ done: false, text: 'finish Svelte tutorial' },
		{ done: false, text: 'build an app' },
		{ done: false, text: 'world domination' }
	];

	function add() {
        // `concat` returns a new array while `push` returns the length of updated array.
		todos = todos.concat({ done: false, text: '' });

        // So above is the exact same as below
/*
        todos.push({ done: false, text: '' });
        todos = todos;
*/
        // `concat` is less efficient than `push` if used in normal circumstances
        // However, since we have to reassign todo anyway if we use `push`, we might as well 
        // use `concat` instead, as it's better to have your application a millisecond slower
        // and avoid bugs that waste your time because you forgot to write "todos = todos;"
        
        // Milliseconds are really only important when coding a server, not a client
	}

	function clear() {
        // In this case, `filter` returns a new array that consists of only tasks that are not marked
        // as done. Because a new array is returned instead of mutating an existing array, "todos = todos;"
        // is NOT required.
		todos = todos.filter(task => !task.done);
	}

    // Get only the number tasks that are not marked as complete 
	$: remaining = todos.filter(task => !task.done).length;
</script>

<h1>Todos</h1>

<!-- Loop through todos -->
{#each todos as todo}
	<div>
        <!-- 
            You can bind not only variables and whole objects,
            but also object properties as you can see
         -->
		<input
			type=checkbox
			bind:checked={todo.done}
		>

		<input
			placeholder="What needs to be done?"
			bind:value={todo.text}
			disabled={todo.done}
		>
	</div>
{/each}

<p>{remaining} remaining</p>

<button on:click={add}>
	Add new
</button>

<button on:click={clear}>
	Clear completed
</button>
