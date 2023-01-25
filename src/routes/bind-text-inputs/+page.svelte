<script>
    // Remember, an empty string is falsy
	let name = '';
    $: databaseName = name.replaceAll(" ", "_");
</script>

<input bind:value={name} placeholder="enter your name">
<!-- If name is empty (falsy) display 'stranger', otherwise display name -->
<p>Hello {name || 'stranger'}!</p>

<!-- 
    Some databases may need to remove spaces from the name. 
    Lets simulate this on the front end.
 -->
<sub>{databaseName}</sub>