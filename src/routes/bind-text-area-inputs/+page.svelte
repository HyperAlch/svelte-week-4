<script>
    // Default content
	let text = `Some words are <i>italic</i>, some are <b>bold</b>`;
</script>
<h1>Type HTML</h1>
<!-- Bind... -->
<textarea bind:value={text}></textarea>

<!-- Display as html -->
{@html text}

<style>
	textarea { width: 100%; height: 200px; margin-bottom: 50px;}
</style>
