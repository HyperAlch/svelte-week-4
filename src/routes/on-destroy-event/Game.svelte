<script>
    import { createEventDispatcher, onDestroy } from 'svelte';
    export let name;

    const dispatch = createEventDispatcher();

    const deleteMe = () => dispatch('delete', {
        name: name,
    });

    onDestroy(() => {
		console.log(`${name} was shutdown by the publisher.`);
	});
</script>

<li>
    <a href="/" on:click|preventDefault={deleteMe}>{name}</a>
</li>