<script>
    // Changing the default value to 1, 2, or 3 will reflect a change in UI itself.
    // Try it!
	let scoops = 1;

    let menu = [
		'Cookies and cream',
		'Mint choc chip',
		'Raspberry ripple'
	];

    // You could add more Flavors as the default value.
    // We could even give and empty array to select no values by default.
    // This will reflect a change in UI itself.
    // Try it!
	let flavours = [menu[1]];

	
    // Some string manipulation
	function join(flavours) {
        // We can use an if-guard here instead of a full if-else statement set because both 
        // logic paths return something.
		if (flavours.length === 1) return flavours[0];
		return `${flavours.slice(0, -1).join(', ')} and ${flavours[flavours.length - 1]}`;
	}
</script>

<h2>Size</h2>
<!-- `bind:group` can be used for both radio and checkbox elements-->

<!-- Here we bind all 3 inputs to `scoops` and hard code the values -->
<label>
	<input type=radio bind:group={scoops} value={1}>
	One scoop
</label>

<label>
	<input type=radio bind:group={scoops} value={2}>
	Two scoops
</label>

<label>
	<input type=radio bind:group={scoops} value={3}>
	Three scoops
</label>

<h2>Flavours</h2>

<!-- 
    Here we loop through the menu options, bind `flavours`, 
    then use the elements in menu to represent both the value and UI label for each
-->
{#each menu as flavour}
	<label>
		<input type=checkbox bind:group={flavours} value={flavour}>
		{flavour}
	</label>
{/each}

<!-- No flavours selected -->
{#if flavours.length === 0}
	<p>Please select at least one flavour</p>

<!-- To many flavours selected -->
{:else if flavours.length > scoops}
	<p>Can't order more flavours than scoops!</p>

<!-- Correct amount of flavours selected -->
{:else}
	<p>
		You ordered {scoops} {scoops === 1 ? 'scoop' : 'scoops'}
		of {join(flavours)}
	</p>
{/if}
