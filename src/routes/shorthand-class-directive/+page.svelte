<script>
	let big = false;
</script>

<label>
	<input type=checkbox bind:checked={big}>
	big
</label>

<!-- Full implementation -->
<div class:big="{big === true}">
	some {big ? 'big' : 'small'} text
</div>

<!-- Semi Shorthand -->
<div class:big="{big}">
	some {big ? 'big' : 'small'} text
</div>

<!-- Full Shorthand -->
<div class:big>
	some {big ? 'big' : 'small'} text
</div>

<style>
	.big {
		font-size: 4em;
	}
    
    label {margin-bottom: 20px;display: block;}
</style>