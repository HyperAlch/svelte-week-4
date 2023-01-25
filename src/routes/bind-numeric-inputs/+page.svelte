<script>
    // We can set any value for our default bind variable
    // It doesn't have to be a blank string or 0
    
    // Just make sure it doesn't break the application. For example, setting the default number to 15
    // when the max value enforced by the UI is 10
	let a = 10;
	let b = 2;
</script>

<div>
	<input type=number bind:value={a} min=0 max=10>
	<input type=range bind:value={a} min=0 max=10>
</div>
<br>
<div>
	<input type=number bind:value={b} min=0 max=10>
	<input type=range bind:value={b} min=0 max=10>
</div>

<p>{a} + {b} = {a + b}</p>