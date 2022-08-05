<script>
	import { fade } from 'svelte/transition';

	let books = ['Learning Svelte', 'The Zen of Cooking Tea'];
	let newBook = '';

	function addBook(evt) {
		if (evt.key === 'Enter') {
			// need to reset the books variable vs. simply pushing a value on - otherwise svelte won't know that value has been updated
			books = [...books, newBook];

			newBook = '';
		}
	}
</script>

<div>
	<h1>My Little Book App</h1>
	<h4>Add Book</h4>
	<input type="text" bind:value={newBook} on:keydown={addBook} />
	<h4>My Books</h4>
	<ul>
		{#each books as book}
			<li transition:fade>{book}</li>
		{/each}
	</ul>
</div>

<style>
	* {
		font-family: 'Arial';
		color: white;
		text-align: center;
	}
	input {
		padding: 5px 10px;
		margin: auto;
		position: relative;
		border: 1px solid turquoise;
	}
	li {
		list-style: none;
	}
	ul {
		padding: 5px 0;
	}
	h1 {
		color: white;
		background-color: turquoise;
		font-weight: bolder;
		padding: 5px 0px;
	}
	h4 {
		color: white;
		font-weight: bold;
		text-align: center;
		padding: 5px 0px;
	}
	div {
		position: relative;
		background-image: linear-gradient(rgba(48, 213, 200, 1), rgba(48, 213, 200, 0));
		height: 1000px;
	}
</style>
