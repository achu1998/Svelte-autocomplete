<script>
	export let name;
	export let search = '';
	let fruits = ['apple','mango','orange','avocado','pineapple','grapes'];
		
</script>

<main>
	<h1>Enjoy {name}!</h1>
	<p><input bind:value={search} list="fruits" name="fruit" id="fruit" placeholder="Search Fruits" ></p>
	<datalist id="fruits">	
	{#each fruits as item}
		{#if item.slice(0,search.length) == search.toLowerCase()}
			<option value={item}></option>
		{/if}
	{/each}
</datalist>

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>