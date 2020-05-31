<script>
    import Thing from './Thing.svelte';


    let user = {loggedIn: false };

    function toggle() {
        user.loggedIn = !user.loggedIn;
    }


    let x = 7;


    let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];


    let things = [
        { id: 1, color: '#0d0887' },
		{ id: 2, color: '#6a00a8' },
		{ id: 3, color: '#b12a90' },
		{ id: 4, color: '#e16462' },
		{ id: 5, color: '#fca636' }
	];
    function handleClick() {
        things = things.slice(1);
    }


    let promise = getRandomNumber();

    async function getRandomNumber() {
		const res = await fetch(`https://svelte.dev/tutorial/random-number`);
		const text = await res.text();

		if (res.ok) {
			return text;
		} else {
			throw new Error(text);
		}
	}

	function handleClick2() {
		promise = getRandomNumber();
	}
</script>

{#if user.loggedIn}
  <button on:click={toggle}>
    Log out
  </button>
{:else}
  <button on:click={toggle}>
    Log in
  </button>
{/if}


{#if x > 10}
  <p>{x} is greater than 10</p>
{:else if 5 > x}
  <p>{x} is less than 5</p>
{:else}
  <p>{x} is between 5 and 10</p>
{/if}


<h3>The Famous Cats of Youtube</h3>
<ul>
    {#each cats as {id, name}, i}
      <li><a target="_blank" href="https://www.youtube.com/watch?v={id}">
        {i + 1}: {name}
      </a></li>
    {/each}
</ul>


<button on:click={handleClick}>
	Remove first thing
</button>
{#each things as thing (thing.id)}
	<Thing current={thing.color}/>
{/each}


<button on:click={handleClick2}>
	generate random number
</button>

{#await promise}
	<p>...waiting</p>
{:then number}
	<p>The number is {number}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}