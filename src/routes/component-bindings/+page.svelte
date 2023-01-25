<script>
	import Keypad from './Keypad.svelte';

	let pin;

    // Replace every number except the newest with a dot
	$: view = pin ? pin.replace(/\d(?!$)/g, '•') : 'enter your pin';

	function handleSubmit() {
		alert(`submitted ${pin}`);
	}
</script>

<!-- Change the color of the display depending on if `pin` is truthy or not -->
<h1 style="color: {pin ? '#333' : '#ccc'}">{view}</h1>

<!-- Notice how we are binding to a property that is declared in the Keypad component itself -->
<Keypad bind:value={pin} on:submit={handleSubmit}/>