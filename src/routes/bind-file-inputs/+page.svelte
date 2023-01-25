<script>
	let files;

	$: if (files) {
		// Note that `files` is of type `FileList`, not an Array:
		// https://developer.mozilla.org/en-US/docs/Web/API/FileList
		for (const file of files) {
			console.log(`${file.name}: ${file.size} bytes`);
		}
	}
</script>

<label for="avatar">Upload a picture:</label>
<!-- Accept only a single image -->
<input
	accept="image/png, image/jpeg"
	bind:files
	id="avatar"
	name="avatar"
	type="file"
/>
<br><br>

<label for="many">Upload multiple files of any type:</label>
<!-- Except multiple of any file type-->
<input
	bind:files
	id="many"
	multiple
	type="file"
/>

{#if files}
	<h2>Selected files:</h2>
    <!-- 
        Here we take a FileList object and convert it into an array 
        so we can iterate through it using Svelte's `each` block 
    -->
	{#each Array.from(files) as file}
		<p>{file.name} ({file.size} bytes) </p>
	{/each}
{/if}

<style>
    label {
        display: block;
    }
</style>