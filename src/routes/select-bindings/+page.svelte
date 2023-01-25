<script>
	let questions = [
		{ id: 1, text: `Where did you go to school?` },
		{ id: 2, text: `What is your mother's name?` },
		{ id: 3, text: `What is another personal fact that an attacker could easily find with Google?` }
	];

    // Notice how `selected` doesn't need a default values
    // The first and default selection in the UI dropdown will automatically bind to `selected` 
	let selected;

	let answer = '';

	function handleSubmit() {
        // Because selected points to an Object (see below) instead of a primitive, we can get
        // both the id and text properties of selected
		alert(`answered question ${selected.id} (${selected.text}) with "${answer}"`);
	}
</script>

<h2>Insecurity questions</h2>

<form on:submit|preventDefault={handleSubmit}>
    <!-- 
        Bind `selected` to the select element
        Also, when a new question is selected, clear the old text input for a better user experience
     -->
	<select bind:value={selected} on:change="{() => answer = ''}">
        <!-- Loop through our questions -->
		{#each questions as question}
            <!-- 
                Notice how we are using an Object as the value instead of a 
                primitive value like String or Number.
            -->
			<option value={question}>
                <!-- Display only the text of the object and not the whole thing -->
				{question.text}
			</option>
		{/each}
	</select>

    <!-- Bind to answer -->
	<input bind:value={answer}>

    <!-- Keep the button disabled unless `answer` is truthy -->
	<button disabled={!answer} type=submit>
		Submit
	</button>
</form>

<p>selected question {selected ? selected.id : '[waiting...]'}</p>

<style>
	input { display: block; width: 500px; max-width: 100%; margin-bottom: 15px; margin-top: 15px;}
</style>