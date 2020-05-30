<script>
	export let name;

	let src = "image-1.gif";
	let alt_name="A man";

	import Nested from './Nested.svelte';

	let count = 0;
	$: doubled = count * 2;
	function handleClick() {
		count += 1;
	}
</script>

<main>
	<h1>Hello {name.toUpperCase()}!</h1>

	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<Nested/>

	<img {src} alt="{alt_name} dances.">
</main>

<button on:click={handleClick}>
	Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		/*text-transform: uppercase;*/
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	p {
		color: purple;
		font-family: 'Comic Sans MS', cursive;
		font-size: 2em;
	}
</style>