<script>
	let current = 'foo';
</script>

<!-- Make the class "activeState" toggle based of an === statement -->
<button
	class:activeState="{current === 'foo'}"
	on:click="{() => current = 'foo'}">foo</button>

<button
	class:activeState="{current === 'bar'}"
	on:click="{() => current = 'bar'}">bar</button>

<button
	class:activeState="{current === 'baz'}"
	on:click="{() => current = 'baz'}">baz</button>

<style>
	button {
		display: block;
        width: 70px;
        height: 50px;
        margin: 20px;
	}

	.activeState {
		background-color: #ff3e00;
		color: white;
	}
</style>