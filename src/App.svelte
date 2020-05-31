<script>
	export let name;

	let src = "image-1.gif";
	let alt_name = "A man";

	import Nested from './Nested.svelte';
	import Nested2 from './Nested2.svelte';
	import Info from './Info.svelte';
	import LogicTuts from './LogicTuts.svelte';
	import EventsTuts from './EventsTuts.svelte';
	import BindingsTuts from './BindingsTuts.svelte';
	import CustomStores from './CustomStores.svelte';
	import TransitionsTuts from './TransitionsTuts.svelte';
	import AnimationsTuts from './AnimationsTuts.svelte';
	import ClassesTuts from './ClassesTuts.svelte';
	import SpecialElemsTuts from './SpecialElemsTuts.svelte';
	import SpecialElemsTuts2 from "./SpecialElemsTuts2.svelte";

	let count = 0;
	$: doubled = count * 2;
	$: if (count >= 10) {
		alert('count is dangerously high');
		count = 9;
	}

	function handleClick() {
		count += 1;
	}

	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers = [...numbers, numbers.length + 1];
	}

	$: sum = numbers.reduce((t, n) => t + n, 0);

	const pkg = {
		name: 'svelte',
		version: 3,
		speed: 'blazing',
		website: 'https://svelte.dev'
	};

</script>

<main>
	<h1>Hello {name.toUpperCase()}!</h1>

	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<Nested/>

	<img {src} alt="{alt_name} dances.">
</main>

<hr/>
<button on:click={handleClick}>
	Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>

<hr/>
<p>{numbers.join(' + ')} = {sum}</p>
<button on:click={addNumber}>
	Add a number
</button>

<hr/>
<Nested2 answer="{42}"/>
<Nested2/>

<hr/>
<Info {...pkg}/>
<!--   translates into...
<Info name={pkg.name} version={pkg.version} speed={pkg.speed} website={pkg.website}/>
-->


<hr/>
<h2>Logic</h2>
<LogicTuts/>


<hr/>
<h2>Events</h2>
<EventsTuts/>


<hr/>
<h2>Bindings</h2>
<BindingsTuts/>


<hr/>
<h2>Custom stores</h2>
<CustomStores/>


<hr/>
<h2>Transitions</h2>
<TransitionsTuts/>


<hr/>
<h2>Animations</h2>
<AnimationsTuts/>


<hr/>
<h2>Classes</h2>
<ClassesTuts/>


<hr/>
<h2>Special elements</h2>
<SpecialElemsTuts/>

<hr/>
<h2>Special elements cont...</h2>
<SpecialElemsTuts2/>

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